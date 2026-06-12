---
title: "error while upgrading to edgy"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by sblanzio on 2006-10-28
I am upgrading from dapper to edgy in the official way. It has downloaded for 3 hours and now, while it says I havw 25 minutes left to complete installation it stopped with this error:

```

Unpacking replacement vino ...
Preparing to replace xsane 0.97-4ubuntu6 (using .../xsane_0.99+0.991-1ubuntu2_i386.deb) ...
Unpacking replacement xsane ...
Preparing to replace xsane-common 0.97-4ubuntu6 (using .../xsane-common_0.99+0.991-1ubuntu2_all.deb) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "it_IT:it:en_GB:en",
        LC_ALL = (unset),
        LANG = "it_IT.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Unpacking replacement xsane-common ...
Preparing to replace zenity 2.14.3-0ubuntu1 (using .../zenity_2.16.1-0ubuntu1_i386.deb) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "it_IT:it:en_GB:en",
        LC_ALL = (unset),
        LANG = "it_IT.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Unpacking replacement zenity ...
Selecting previously deselected package ubuntu-desktop.
Unpacking ubuntu-desktop (from .../ubuntu-desktop_1.30_i386.deb) ...
Preparing to replace uim-utils 1:1.0.0-1ubuntu1 (using .../uim-utils_1%3a1.2.1-3ubuntu2_i386.deb) ...
Unpacking replacement uim-utils ...
Preparing to replace uim-common 1:1.0.0-1ubuntu1 (using .../uim-common_1%3a1.2.1-3ubuntu2_all.deb) ...
ERROR: unbound variable (errobj is-set-ugid?)

*backtrace*
>>(is-set-ugid?)
>>(if (is-set-ugid?) (list (string-append (sys-pkglibdir) "/plugin")) (filter string? (append (list (getenv "LIBUIM_PLUGIN_LIB_DIR") (string-append (getenv "HOME") "/.uim.d/plugin") (string-append (sys-pkglibdir) "/plugin")) (if (getenv "LD_LIBRARY_PATH") (string-split (getenv "LD_LIBRARY_PATH") ":") ()))))
>>(define uim-plugin-lib-load-path (if (is-set-ugid?) (list (string-append (sys-pkglibdir) "/plugin")) (filter string? (append (list (getenv "LIBUIM_PLUGIN_LIB_DIR") (string-append (getenv "HOME") "/.uim.d/plugin") (string-append (sys-pkglibdir) "/plugin")) (if (getenv "LD_LIBRARY_PATH") (string-split (getenv "LD_LIBRARY_PATH") ":") ())))))
>>(require "plugin.scm")
>>(require "init.scm")
>>(*catch (quote errobj) (require "init.scm"))
>>(eq? (quote *init.scm-loaded*) (*catch (quote errobj) (require "init.scm")))

ERROR: unbound variable (errobj custom-reload-customs)

ERROR: unbound variable (errobj custom-choice-rec-sym)

ERROR: unbound variable (errobj plugin-alist)

ERROR: wta to car (errobj t)


```

how can i fix this and recover my installation!?

I am not sure, what can i do?

thanks

EDIT:
see the 4th post for a workaround

---

### Post by sblanzio on 2006-10-28
I tried to presso CTRL+C and it gone for about a minute.
then I got a "fatal error" that I couldn't copy and paste here because everything disappeared.

Now I have a system that doesn't work properly and I don't know how to recover and fix my installation.

now if I try restarting the upgrade I get this error:

```

enrico@enrico-desktop:~$ gksudo "update-manager -c"

(gksudo:16602): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Fontconfig error: Cannot load default config file
  File "/usr/bin/update-manager", line 25, in ?
    import pygtk
ImportError: No module named pygtk
enrico@enrico-desktop:~$

```


i'm not so glad I decided to upgrade....

---

### Post by systemgod on 2006-10-28
Yep, got exactly the same problem. uim-utils screwed up. After pressing Ctrl-C it seems to be going along fine for me, however I see a lot of messages complaining about locale settings.

sblanzio, can you try 'gksu "apt-get -f install"' that should clean up a broken install procedure.

Nico

---

### Post by sblanzio on 2006-10-28
Well, in fact if I pressed ctrl-c it seemed to get better but it just gave more error messages.

I finally "solved" this problem deleting everything I found in 
/usr/share/uim/

I know this is not a true solution but I really think that this is a bug, and I didn't know what to do.

I tried the command you suggest and many many others I found on the internet but I NEVER had a different result.

Now the new uim version is properly installed.

good luck!! ;)

---

### Post by systemgod on 2006-10-28
I noticed the same in the mean time (the upgrade was still running when I wrote the previous post). The upgrade ended with a few packages not installable due to uim-common. The trick with 'apt-get -f install' doesn't work indeed. uim-common can't even be removed properly. sigh.

I'm going to try your suggestion by removing everything in /usr/share/uim/ now.

Nico

---

### Post by systemgod on 2006-10-28
Got some scary messages while reinstalling uim-common but now everything seems to work.

Thanks (for solving your own problem and mine at the same time ;) )

Nico

---

### Post by flipkick on 2006-10-30
Have the same problem. But i don't want to delete any files. I think on my machnie it breaks wit libcairo.... but the error is the same....

---

