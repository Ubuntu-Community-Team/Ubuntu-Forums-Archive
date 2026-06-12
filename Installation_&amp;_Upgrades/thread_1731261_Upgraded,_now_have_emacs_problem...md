---
title: "Upgraded, now have emacs problem.."
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by meburke on 2011-04-16
Since I've upgraded to 10.4 I've been getting this error from dpkg:

Recompiling Common Lisp Controller for ecl
/usr/lib/common-lisp/bin/ecl.sh loading and dumping clc.
;;; Loading "/usr/lib/ecl/install-clc.lisp"
;;; Loading #P"/usr/lib/ecl-9.6.1/cmp.fas"
;;; Loading #P"/usr/lib/ecl-9.6.1/sysfun.lsp"

Saving to new-ecl...
;;; Loading "/var/cache/common-lisp-controller/0/ecl/common-lisp-controller/common-lisp-controller.fas"
;;; Loading "/var/cache/common-lisp-controller/0/ecl/cl-asdf/asdf.fas"

The function SYSTEM-SOURCE-FILE is undefined.
Available restarts:

1. (QUIT-DEBUGGER) Quit debugger level 1.
2. (ABORT) ABORT

Top level.
ASDF> 

The problem is that it seems to hang here. I cannot quit the debugger nor abort, and I have to use Ctl-C to get out of it, which apparently interrupts dpkg and causes a crash.

Does anyone know what I'm supposed to require at the ASDF prompt?

Alternatively, does anyone know how I can uninstall all the emacs22 and 23 (including add-ons and plug-ins) without ruining my upgraded installation, and then configure dkpg to ignore the list so I can install emacs23 from scratch?

After my last attempt (which munged my whole OS), I restored my backed-up 9.10 and removed (I thought) all emacs and related goodies. For some reason, that didn't prevent the problem from recurring on upgrading to the LTS.

Thank you,

Mike

---

### Post by mörgæs on 2011-04-17
Have you thought of a clean installation of 10.04.2?

---

### Post by meburke on 2011-04-17
Thought about it, but I dread losing all the customization I've already done. The OS is working fine and I have almost everything I added and upgraded before. I can actually do work. Only my Emacs installation seems somewhat munged, but I can actually still use emacs, so I don't know everything that may be wrong yet.

---

### Post by meburke on 2011-04-17
Here is a copy of the error report:

E: cl-asdf: subprocess installed post-installation script killed by signal (Killed)
E: emacs23: subprocess installed post-installation script returned error exit status 1
E: emacs: dependency problems - leaving unconfigured
E: emacs22-gtk: subprocess installed post-installation script returned error exit status 1
E: goby: dependency problems - leaving unconfigured
E: libatlas3gf-3dnow: subprocess installed post-installation script returned error exit status 30
E: sepia: dependency problems - leaving unconfigured
E: yaml-mode: subprocess installed post-installation script returned error exit status 1

 I get this after killing the cl-asdf script, which hangs up on the ASDF> prompt. As I mentioned, any input at the terminal to the ASDF> prompt is ignored; nothing works, not even the (ABORT) command. I may be missing something important here, but while it sort of looks like it is trying to find the location of the directory where emacs/asdf resides, it seems to find it just fine from emacs itself. The update manager says emacs23 and 22 are unconfigured, but emacs23 works. (I just haven't tested all the boundaries to find out which parts are not working because I haven't had the time.)

Thanks for your help,

Mike

---

### Post by Port 80 on 2011-04-17
Meburke:

I did not have that problem after the upgrade, and I have to research before I can offer even a useless answer.  I too had something show up that was not there before:  When I start emacs in the virtual terminal, I get the 'xemacs' with this error:


** (emacs:9327): CRITICAL **: murrine_style_draw_box: assertion `height >= -1' failed** (emacs:9327): CRITICAL **: murrine_style_draw_box: assertion `height >= -1' failed


Emacs still functions, but it disturbs me.  Of course, I don't get that if I use the -nw option.

I think that there was a library change in 10.04 that causes the bug.

---

