---
title: "Need more administrative privilege with Unity"
date: 2011-11-08
forum: Installation &amp; Upgrades
---

### Post by Randy Schilling on 2011-11-08
Hello -

I'm setting up newly installed U11.10 and working under its Unity
desktop.

I ran into a problem with my installation of TexLive2011.
I chose to install this software by downloading it because
Synaptic offers only the somewhat outdated TexLive2009.

After downloading, I started the installer in a terminal with the command:
        install-tl -gui wizard.
The TexLive installer opens and tries to install to 
    /usr/local/texlive/2011
and returns the message 
   "default not allowed or not writeable - please change."
I did not run into this problem awhile ago when I installed TexLive under U10.04.
I checked that I'm working under an administrator account.
I tried starting the installer with the command:
        sudo install-tl -gui wizard
and got a "command not found" error.

I think this means that some permissions need to be changed but I want to check with you to see if there is a more global way of improving my administrative privileges.

Thanks and regards - Randy

---

### Post by snowpine on 2011-11-08
Try it with the full path to the file, and use 'gksu' if it's a graphical application, for example:

```
gksu /home/randy/Downloads/install-tl -gui wizard
```

---

### Post by Randy Schilling on 2011-11-08
snowpine:
I tried the command
    gksu ~/Downloads/install-tl-20111108/Downloads/install-tl -gui wizard
and got a message box with,
                   user i does not exist,
and the following warning at the terminal,
    (gksu:6244): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap".
Also, TexLive's instructions tell us to move to the folder containing install-tl
(so the full path is probably not necessary)
and to add the current folder to the PATH variable with the command,
    PATH=.:$PATH.
Thanks for your interest, further ideas welcome.

---

### Post by Randy Schilling on 2011-11-08
I tried logging in as root user with the command,
    sudo passwd root,
started the TexLive installer as before,
        install-tl -gui wizard,
the installer opened and gave the same response as before,
   "default not allowed or not writeable - please change."

---

### Post by snowpine on 2011-11-08
I am not familiar with TexLive to diagnose the problem, but I'm sure the solution is not to relax security settings.

Is there possibly a README or INSTALL file you have overlooked?

---

### Post by Randy Schilling on 2011-11-09
Snowpine, thanks for your interest.  I missed a period.  My command should have been

./install-tl -gui wizard.

You're right, it's not a privilege issue.  Thanks again and regards - Randy

---

