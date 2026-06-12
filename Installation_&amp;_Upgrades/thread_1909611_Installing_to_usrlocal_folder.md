---
title: "Installing to /usr/local folder"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by godfreypilot on 2012-01-15
Hey all,

Apologies in advance, I am brand new to Ubuntu (and Linux in general), so this may be a stupid question, but here goes:

I'm trying to install Matlab off of a CD (the primary reason for downloading Ubuntu to begin with).  I want to make the install path the /usr/local folder, but i can't do that without sudo privileges.

Any way to get sudo privileges within the installer?  Or is it best to install to some other location (say the Desktop) and then copy the folder into the /usr/local directory using sudo commands in the terminal or through a sudo window in nautilus?

Also, once I get everything installed, can I just launch Matlab by using the "matlab -desktop" command in the terminal?  Or is some additional configuration required?

Thanks for all the help,

Robby

---

### Post by Mark Phelps on 2012-01-16
Sorry for asking the obvious ... but ... CD versions of apps are nearly always for MS Windows.  So, you sure this CD is for Linux?

Also, how are you trying to install?

You should be installing from the Software Center, or barring that, from a .deb.

If you're installing from source, I believe you need to be root to make the executable anyway.

---

### Post by godfreypilot on 2012-01-16
> **Mark Phelps said:**
> Sorry for asking the obvious ... but ... CD versions of apps are nearly always for MS Windows.  So, you sure this CD is for Linux?

Also, how are you trying to install?

You should be installing from the Software Center, or barring that, from a .deb.

If you're installing from source, I believe you need to be root to make the executable anyway.

The CD I'm using is cross-platform, and contains an installer specifically for linux.

I figured out the problem... i needed to launch the installer shell using the command "sudo sh /media/MATLAB/install", which allows the installer to write files with superuser privileges.

I was also having trouble running the program once installed (the command "matlab" didn't work), but I found out that was because the installer wasn't creating symbolic links in the /usr/local/bin folder.  Instead I need to navigate directly to the executable in the /usr/local/ directory.

---

