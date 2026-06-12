---
title: "Restricted repository..."
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by Xyzzy on 2006-07-07
When I do an initial install the system is set up to draw packages from main (of course) and restricted. I think this is because my modem (which I don't use) needs a restricted driver.

How can I tell Ubuntu to only use main? I can, of course, uninstall the restricted modules and edit sources.lst, but I'd like to fix it from the get go.

Unrelated: vrms reports ttf-gentium as nonfree. What's the deal with that?

---

### Post by aysiu on 2006-07-07
Main and Restricted should not have redundant packages.

If a package exists in Main, it'll be pulled from Main.

If a package exist in Restricted, it'll be pulled from Restricted.

What's the exact name of the package you're installing?

---

### Post by Xyzzy on 2006-07-08
I'm just doing a standard installation.

After I finish the basic installation, I add universe to sources.lst and I install vrms:

> Setting up vrms (1.11) ...

An invocation of vrms has been added to the set of cron jobs run on a
monthly basis, so that you will get a periodic reminder of non-free
packages which are installed on your system.  Here is the current list:

               Non-free packages installed on ubuntu

linux-386                 Complete Linux kernel on 386.
linux-restricted-modules- Non-free Linux 2.6.15 modules on 386
linux-restricted-modules- Non-free Linux 2.6.15 modules on 386
linux-restricted-modules- Restricted Linux modules on 386.
linux-restricted-modules- Non-free Linux 2.6.15 modules helper script

  5 non-free packages, 0.5% of 1037 installed packages.

BTW, this isn't the *exact* message I get. But it is very similar.

Now, I can remove all those restricted modules just fine. And I have.

I'd like to know how to invoke the installer *without* the restricted repository enabled.

---

### Post by aysiu on 2006-07-08
The restricted repository is enabled by default. The only way to turn it off is to, as you said before, edit your sources.list file and remove it.

---

### Post by Xyzzy on 2006-07-08
[http://archives.free.net.ph/message/20060614.083219.1a6c53e8.en.html](http://archives.free.net.ph/message/20060614.083219.1a6c53e8.en.html)

Maybe I can edit it before it starts pulling in packages, during the install.

IMO, this seems to be a significant flaw in Ubuntu. Debian offers me a choice.

BTW, running the install as "expert" did not allow me to choose the repository either.

:(

---

### Post by aysiu on 2006-07-08
> **Xyzzy said:**
> [http://archives.free.net.ph/message/20060614.083219.1a6c53e8.en.html](http://archives.free.net.ph/message/20060614.083219.1a6c53e8.en.html)

Maybe I can edit it before it starts pulling in packages, during the install.

IMO, this seems to be a significant flaw in Ubuntu. Debian offers me a choice.

BTW, running the install as "expert" did not allow me to choose the repository either.

:(
It's not a significant flaw. It's a different approach and a different target audience.

If you like the way Debian's installer works, you can use Debian. That's the beauty of choice.

---

### Post by az on 2006-07-08
> **Xyzzy said:**
> [http://archives.free.net.ph/message/20060614.083219.1a6c53e8.en.html](http://archives.free.net.ph/message/20060614.083219.1a6c53e8.en.html)

IMO, this seems to be a significant flaw in Ubuntu. Debian offers me a choice.


:(

You can't install without getting linux-restricted-modules, but after you install, you can run

sudo apt-get remove linux-restricted-modules*

and you will have a clean system.  You can even enable the universe repos and still have a clean (GPL-compatible) system.

It is a design goal for the system installer to be simple.  That's why you are not explicitly offered the choice during the install.  It's a hassle to include the non-free stuff, but it is also packaged very carefuly to be easily removed.  That, too, is a design goal (AFAIK).

---

