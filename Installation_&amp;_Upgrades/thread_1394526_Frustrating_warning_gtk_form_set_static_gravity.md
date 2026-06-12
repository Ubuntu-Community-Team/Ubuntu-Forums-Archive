---
title: "Frustrating warning: gtk_form_set_static_gravity"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by Hguest on 2010-01-30
Hi, folks:
    I'm having problems with my gvim.
    My platform is Ubuntu 9.10, with the latest gvim version. I've been having annoying warnings every time I open gvim:

(gvim:8878): GLib-WARNING **: g_set_prgname() called multiple times

** (gvim:8878): CRITICAL **: gtk_form_set_static_gravity: assertion `static_gravity_supported' failed

** (gvim:8878): CRITICAL **: gtk_form_set_static_gravity: assertion `static_gravity_supported' failed

** (gvim:8878): CRITICAL **: gtk_form_set_static_gravity: assertion `static_gravity_supported' failed

** (gvim:8878): CRITICAL **: gtk_form_set_static_gravity: assertion `static_gravity_supported' failed

** (gvim:8878): CRITICAL **: gtk_form_set_static_gravity: assertion `static_gravity_supported' failed


     Two types of warnings: 1. g_set_progname called multiple times;
                            2. static gravity


For problem tow, I find a solution on the web, but the solution is for debian. The problem with this solution is, I don't even have the file "gui_gtk_f.c" that is proposed to be changed. Does anyone know what is the corresponding file on Ubuntu 9.10 that I make the changes? (Please let me know the changes if they are supposed to be different from what is proposed here: [http://ftp.vim.org/pub/vim/patches/7.2/7.2.257](http://ftp.vim.org/pub/vim/patches/7.2/7.2.257))


For problem one, I'm in the similar situation. Here is what is proposed:
[http://git.gnome.org/browse/glib/commit/?id=3dab24828edd8ebfd6d6c8bb20c181fc0d5650a1](http://git.gnome.org/browse/glib/commit/?id=3dab24828edd8ebfd6d6c8bb20c181fc0d5650a1)

But I don't have the gutils.c file!


Can someone out there help?

Any suggestion is appreciated.

Thanks in advance.

---

### Post by redearth on 2010-02-27
I'm having the same problem, as I'm sure many others are. I'm also having a difficult time with the instructions I've found on the web and can't figure out how to solve the problem for Ubuntu 9.10.

---

### Post by redearth on 2010-02-27
Okay, while waiting for vim to be updated in Ubuntu, I just added this as a bash alias since I don't need any output from gvim anyway:

alias gvim="gvim 2>/dev/null"

---

### Post by Hguest on 2010-12-03
> **redearth said:**
> Okay, while waiting for vim to be updated in Ubuntu, I just added this as a bash alias since I don't need any output from gvim anyway:

alias gvim="gvim 2>/dev/null"

Yep, you're the man.
Sorry about the late reply, though.

---

