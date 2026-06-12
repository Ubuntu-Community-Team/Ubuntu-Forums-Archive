---
title: "LAMP + Desktop"
date: 2006-07-30
forum: Installation &amp; Upgrades
---

### Post by racer on 2006-07-30
Hi

I've searched the forums and have found ways to do this, but none which answer my specific question, which is as follows:

I have both the standard Ubuntu 6.06 (LiveCD as sent by Ship-It) as well as the Server Version 6.06 (downloaded ISO).

I've installed a LAMP server, and now wish to add a GUI, which I've attempted to do using "apt-get install ubuntu-desktop"

It all works fine, except the system is trying to download almost 500MB, whereas I'm sure all the required content should already be on my LiveCD.  I've tried adding the LiveCD to sources.list using "apt-cdrom add" but the system still ignores that and downloads the required files.

Is there any way to use the LiveCD in this scenario?  I'm on a slow connection at home and really don't want to spend all day downloading 500mb :(

If this cannot be done, I'll reinstall from scratch using suggestions on other threads about this - but I'm hoping someone will know if using the LiveCD in this way is possible.

tks
roger

---

### Post by Lord Illidan on 2006-07-30
> **racer said:**
> Hi

I've searched the forums and have found ways to do this, but none which answer my specific question, which is as follows:

I have both the standard Ubuntu 6.06 (LiveCD as sent by Ship-It) as well as the Server Version 6.06 (downloaded ISO).

I've installed a LAMP server, and now wish to add a GUI, which I've attempted to do using "apt-get install ubuntu-desktop"

It all works fine, except the system is trying to download almost 500MB, whereas I'm sure all the required content should already be on my LiveCD.  I've tried adding the LiveCD to sources.list using "apt-cdrom add" but the system still ignores that and downloads the required files.

Is there any way to use the LiveCD in this scenario?  I'm on a slow connection at home and really don't want to spend all day downloading 500mb :(

If this cannot be done, I'll reinstall from scratch using suggestions on other threads about this - but I'm hoping someone will know if using the LiveCD in this way is possible.

tks
roger

I am hazarding a guess here.

The live cd is not an install cd in the true sense of the word. Whereas other installers might unpack .deb files and .rpm files, the live cd just copies its content to the harddrive for reasons of space.
Thus you can't get any debs from it, because there aren't any.

---

### Post by az on 2006-07-30
Right, the alternate cd and the server cd are a text-mode installer and a repository filled with all the packages that the installer installs.

The live cd is a live filesystem that gets transplanted onto your drive.  There is only a small repository on that cd with some toolchain and additional network things you may need to build for special circumstances.

If you were dealing with the alternate cd, you would be in business.  

If you really want to save on bandwidth, install the live cd on top of your server (erasing it) and the install the LAMP stack (sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server)

---

### Post by racer on 2006-07-31
ok thanks both, that answers my question.  i'll see if i can download the alternate cd at work today, if not i'll reinstall from scratch as per your suggestion.

thanks again.

---

