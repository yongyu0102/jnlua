# Paths
JDK_DIR=/opt/jdk/jdk1.6.0_19
LUA_LIB_DIR=/usr/lib
LUA_INC_DIR=/usr/include/lua5.1
VERSION=5.1

# Tools
CC=gcc
LD=gcc

# Default arguments
CFLAGS=-c -fno-strict-aliasing -fPIC -O2 -Wall -DNDEBUG -D_REENTRANT -DLUA_USE_LINUX
LDFLAGS=-shared

# Description blocks
all: libjnlua$(VERSION).so

libjnlua$(VERSION).so: jnlua.o
	$(LD) $(LDFLAGS) -Wl,-soname=libjnlua$(VERSION).so -olibjnlua$(VERSION).so -L$(LUA_LIB_DIR) -lc -llua$(VERSION) jnlua.o

jnlua.o: ../jnlua.c
	$(CC) $(CFLAGS) -I$(JDK_DIR)/include -I$(JDK_DIR)/include/linux -I$(LUA_INC_DIR) ../jnlua.c

clean:
	-rm libjnlua$(VERSION).so jnlua.o