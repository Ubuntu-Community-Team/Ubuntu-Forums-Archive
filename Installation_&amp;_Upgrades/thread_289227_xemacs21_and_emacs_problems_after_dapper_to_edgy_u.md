---
title: "xemacs21 and emacs problems after dapper to edgy upgrade"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by bhaskar on 2006-10-30
After a dapper to edgy upgrade, both xemacs21 and emacs are broken.

xemacs21 is the most broken:

kbhaskar@bhaskarks:~$ xemacs
Warning: Cannot convert string "-*-helvetica-bold-r-*-*-*-120-*-*-*-*-iso8859-*" to type FontStruct
Warning: Unable to load any usable ISO8859 font
Warning: Unable to load any usable ISO8859 font

Fatal error (11).

Your files have been auto-saved.
Use `M-x recover-session' to recover them.

Your version of XEmacs was distributed with a PROBLEMS file that  may describe
your crash, and with luck a workaround.  Please check it first, but do report
the crash anyway.  Please report this bug by invoking M-x report-emacs-bug,
or by selecting `Send Bug Report' from the Help menu.  If necessary, send
ordinary email to `xemacs-beta@xemacs.org'.  *MAKE SURE* to include the XEmacs
configuration from M-x describe-installation, or equivalently the file
Installation in the top of the build tree.

*Please* try *hard* to obtain a C stack backtrace; without it, we are unlikely
to be able to analyze the problem.  Locate the core file produced as a result
of this crash (often called `core' or `core.<process-id>', and located in
the directory in which you started XEmacs or your home directory), and type

  gdb /usr/bin/xemacs core

then type `where' at the debugger prompt.  No GDB on your system?  You may
have DBX, or XDB, or SDB.  (Ask your system administrator if you need help.)
If no core file was produced, enable them (often with `ulimit -c unlimited'
in case of future recurrance of the crash.

Lisp backtrace follows:

  # bind (frame-being-created)
  make-frame(nil #<x-device on ":0.0" 0x68d>)
  frame-initialize()
  # bind (debugger debug-on-error command-line-args-left)
  command-line()
  # (condition-case ... . ((t (byte-code "      Â" ... 1))))
  # bind (error-data)
  normal-top-level()
  # (condition-case ... . error)
  # (catch top-level ...)

Segmentation fault (core dumped)

But there is no core file.  emacs actually boots, but the screen looks like crap with rectangles instead of characters.

kbhaskar@bhaskarks:~$ emacs
Warning: Cannot convert string "-*-courier-medium-r-*-*-*-120-*-*-*-*-iso8859-*" to type FontStruct
Warning: Unable to load any usable ISO8859 font
Warning: Cannot convert string "-*-helvetica-medium-r-*--*-120-*-*-*-*-iso8859-1" to type FontStruct
Warning: Unable to load any usable ISO8859 font
Warning: Unable to load any usable ISO8859 font

I did not remove any fonts when I upgraded.  Any help in troubleshooting would be greatly appreciated - I'm too old to learn vi!!!

Thanx in advance.

-- Bhaskar

---

### Post by bhaskar on 2006-12-11
After I changed occurrences of /usr/share/X11/fonts to /usr/share/fonts/X11, things now work as expected.

-- Bhaskar

---

### Post by PhilOSparta on 2006-12-15
This is exactly what I needed since my upgrade to Edgy today.  Emacs fonts were really in bad shape.    Now they work properly.

Thanks a million.

Phil

---

### Post by rgrig on 2006-12-20
After my upgrade fonts in emacs look squarish. No warning is printed in the console. What can I do?

---

### Post by bhaskar on 2006-12-20
Read my reply to my original post in this forum as to how I solved the problem.

-- Bhaskar

---

### Post by mish on 2006-12-20
> **bhaskar said:**
> After I changed occurrences of /usr/share/X11/fonts to /usr/share/fonts/X11, things now work as expected.

This was less than clear to me - was it referring to directories or to entries in a config file or what?  I looked for a config file and couldn't find one so I tried the directory approach and it worked.  The exact commands I used were

```

$ sudo mv /usr/share/X11/fonts /usr/share/X11/fonts-empty
$ sudo ln -s /usr/share/fonts/X11 /usr/share/X11/fonts

```

---

### Post by bhaskar on 2006-12-20
Apologies.  I meant in /etc/X11/xorg.conf.

Regards
-- Bhaskar

---

### Post by Skeletor on 2007-01-21
I just installed Ubuntu Edgy Eft from scratch and GNU Emacs 21 from Ubuntu package manager is having the Square font problem.  I tried both of the solutions mentioned here and they both did not seem to change anything.  Anyone else find a root cause of this problem?  Why doesn't Ubuntu fix this by default?

---

### Post by bhaskar on 2007-01-21
Did you restart the X server?

-- Bhaskar

---

### Post by Skeletor on 2007-01-30
Yeah!  That worked.  I realized that when I restarted my computer.  Thanks for your help.

---

