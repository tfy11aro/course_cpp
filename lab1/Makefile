# Define the compiler and the linker. The linker must be defined since
# the implicit rule for linking uses CC as the linker. g++ can be
# changed to clang++.
CXX = g++
CC  = $(CXX)

DEPFLAGS = -MT $@ -MMD -MP -MF $*.d

# Define preprocessor, compiler, and linker flags. Uncomment the # lines
# if you use clang++ and wish to use libc++ instead of GNU's libstdc++.
# -g is for debugging.
CPPFLAGS =  -std=c++11
#CXXFLAGS =  -O2 -Wall -Wextra -pedantic-errors -Wold-style-cast
CXXFLAGS =  -Wall -Wextra -pedantic-errors -Wold-style-cast -fPIC
CXXFLAGS += -std=c++11
CXXFLAGS += -g
CXXFLAGS += $(DEPFLAGS)
LDFLAGS =   -g
LDFLAGS += -L.
LDLIBS = -llab1
#CPPFLAGS += -stdlib=libc++
#CXXFLAGS += -stdlib=libc++
#LDFLAGS +=  -stdlib=libc++

# Targets
PROGS = ltest hello encoding decoding

all: $(PROGS)

# Targets rely on implicit rules for compiling and linking, the following is executed!
# $(CXX) $(CPPFLAGS) $(CXXFLAGS) -c -o $@ $<
# $(CC) $(LDFLAGS) $^ $(LOADLIBES) $(LDLIBS) -o $@
# $@ = the file name of the target of the rule
# $< = The name of the first prerequisite. If the target got its recipe from an implicit rule, this will be the first prerequisite added by the implicit rule.
# $^ = The names of all the prerequisites, with spaces between them.
ltest: ltest.o

hello: hello.o

encoding: encoding.o

decoding: decoding.o

# Phony targets
.PHONY: all clean

# Standard clean
clean:
	rm -f *.o $(PROGS)

# Include the *.d files
# This is some magic, the .d files comprise:
# list.o: list.cc list.h
# list.h:
# Make finds these rules via the $(DEPFLAGS) variable.
SRC = $(wildcard *.cc)
-include $(SRC:.cc=.d)
