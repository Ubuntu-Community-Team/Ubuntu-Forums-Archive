---
title: "Upgraded to LTS 14.04 now cannot start tor"
date: 2015-02-06
forum: Installation &amp; Upgrades
---

### Post by cpcpcp on 2015-02-06
I prevoiusly clicked  to tor run a file called start-tor-browser```
!/bin/sh
#
# GNU/Linux does not really require something like RelativeLink.c
# However, we do want to have the same look and feel with similar features.
#
# To run in debug mode simply pass --debug
#
# Copyright 2011 The Tor Project.  See LICENSE for licensing information.

complain_dialog_title="Tor Browser Bundle"

# First, make sure DISPLAY is set.  If it isn't, we're hosed; scream
# at stderr and die.
if [ "x$DISPLAY" = "x" ]; then
    echo "$complain_dialog_title must be run within the X Window System." >&2
    echo "Exiting." >&2
    exit 1
fi

# Do not (try to) connect to the session manager 
unset SESSION_MANAGER 

# Determine whether we are running in a terminal.  If we are, we
# should send our error messages to stderr...
ARE_WE_RUNNING_IN_A_TERMINAL=0
if [ -t 1 -o -t 2 ]; then
    ARE_WE_RUNNING_IN_A_TERMINAL=1
fi

# ...unless we're running in the same terminal as startx or xinit.  In
# that case, the user is probably running us from a GUI file manager
# in an X session started by typing startx at the console.
#
# Hopefully, the local ps command supports BSD-style options.  (The ps
# commands usually used on Linux and FreeBSD do; do any other OSes
# support running Linux binaries?)
ps T 2>/dev/null |grep startx 2>/dev/null |grep -v grep 2>&1 >/dev/null
not_running_in_same_terminal_as_startx="$?"
ps T 2>/dev/null |grep xinit 2>/dev/null |grep -v grep 2>&1 >/dev/null
not_running_in_same_terminal_as_xinit="$?"

# not_running_in_same_terminal_as_foo has the value 1 if we are *not*
# running in the same terminal as foo.
if [ "$not_running_in_same_terminal_as_startx" -eq 0 -o \
     "$not_running_in_same_terminal_as_xinit" -eq 0 ]; then
    ARE_WE_RUNNING_IN_A_TERMINAL=0
fi

# Complain about an error, by any means necessary.
# Usage: complain message
# message must not begin with a dash.
complain () {
    # Trim leading newlines, to avoid breaking formatting in some dialogs.
    complain_message="`echo "$1" | sed '/./,$!d'`"

    # If we're being run in a terminal, complain there.
    if [ "$ARE_WE_RUNNING_IN_A_TERMINAL" -ne 0 ]; then
        echo "$complain_message" >&2
        return
    fi


```

when I click it now it trys to open the program with an application and this is despite under proerties the permission still shows Allow excecuting file as a program.

Have I mised something obvious?

---

