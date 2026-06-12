---
title: "Install server and deskop"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by mjbrownesq on 2011-07-03
Hi all

I'm a programmer (C/C++/Java) with UNIX/Linux knowledge but not a sys admin and I need some help installing.

I have two laptops (with Vista which I have to keep) and I need to run Ubuntu on both machines as a server and as a desktop for various type of testing.

For example I need to boot one of the laptops in a server mode and the other in a desktop mode then use both in a network to test various software.  However, sometimes I need to boot both in server mode to test other machines, and sometimes I need to boot both in desktop mode.

I am OK with the basics of dual boot systems but I'm not sure the best way to install both server and desktop versions.  I could create enough partitions then do two separate installs; but I'm not keen on doing that.

Is it possible to install both versions in the same partitions and then have two boot options to start in either server or desktop mode?

Can anyone help with advice please?

Thanks.

---

### Post by maclenin on 2011-07-03
I have simply installed one version (desktop) and then added tools to turn the "desktop" into a "sever" (apache / openssh-server / etc) - ad hoc.... I am sure there are millions of ways to slice this...but it doesn't strike me that you need to install both versions on one system - choose one (I would go with desktop) - and configure - on the fly.... Good luck!

---

### Post by mjbrownesq on 2011-07-03
> **maclenin said:**
> I have simply installed one version (desktop) and then added tools to turn the "desktop" into a "sever" (apache / openssh-server / etc) - ad hoc.... 
Thanks maclenin

My only concern is that I want to mimic standard server/desktop installations to mirror the environments I'm working in; ie standard server (with LAMP) and desktop installations with network support.

I need to make sure I get everything you would normally have in a standard server install plus a standard desktop install, rather than installing individual packages; does that make sense?

Cheers.

---

### Post by maclenin on 2011-07-03
**mjbrowneesq!**

Absolutely. I hear you. You've come to the right place to get your question(s) answered - stand-by, I am sure someone in the know will saunter along!

---

### Post by Rocket2DMn on 2011-07-03
If you want you can install the server edition of Ubuntu, then install the "ubuntu-desktop" metapackage to get "both" environments. Also have a look here - [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

Otherwise you will want to setup a dual boot system with a server edition, and a desktop edition. This shouldn't be any more complicated than dual booting with any other OSes. If you need help with that, the forums users here can advise you.  There is no "switching" between editions on a single install - the closest you could do is turn off X at startup, but that wouldn't make it a server installation.

Cheers.

---

### Post by Bachstelze on 2011-07-03
Just install VirtualBox in Windows, then you can have as many different Ubuntu setups as you wish.

---

### Post by maclenin on 2011-07-03
Great tutorials, [here]("http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-11.04-lamp")....

---

### Post by mjbrownesq on 2011-07-03
> **Rocket2DMn said:**
> If you want you can install the server  edition of Ubuntu, then install the "ubuntu-desktop" metapackage to get  "both" environments.
Thanks, so is ubuntu-desktop the only thing that is installed if I did a standalone desktop installation?
> **Rocket2DMn said:**
> Also have a look here - [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)
I  did have a quick look at this, but is seems to be more about having a  GUI in a server environment, rather than a standard desktop environment;  but please correct me if I' wrong!

> **Rocket2DMn said:**
> Otherwise  you will want to setup a dual boot system with a server edition, and a  desktop edition. This shouldn't be any more complicated than dual  booting with any other OSes.
Should I be worried about too many partitions?

I  need to have 5 windows partitions for various requirements; for a  server I would need 7-9 and for a desktop I would need 5-7; that's a lot  of partitions; would it cause problems?

As I'm typing here I  think the end result I want is just two boot systems (Windows and  Linux).  I would set the Ubuntu partitions for a server (/, boot, swap,  usr, var, tmp, opt, srv and home) and then do a complete server  installation.  Then I think I want some way to do a complete desktop  installation in the same partitions; I have no idea how to do this.

The next tricky part (for me  at least), is to then have 3 boot options; windows, server and desktop. I am OK creating multi-boot but don't know how I would configure the boot options to boot into a server or desktop mode;   I would certainly need help with this.

Is any of this sensible or am I talking rubbish?

Cheers.

---

### Post by mjbrownesq on 2011-07-03
> **Bachstelze said:**
> Just install VirtualBox in Windows, then you can have as many different Ubuntu setups as you wish.
Thanks, but I'm not too keen on virtual systems; certainly useful in some situations but I try to avoid them if possible.

Cheers.

---

### Post by drdos2006 on 2011-07-03
Here is how I do my testing under Ubuntu 10.04 LTS.
Gigabyte motherboard, 4 Gig RAM with each virtual OS having 20 Gigs of HDD space. Works fine for me. regards

---

### Post by Rocket2DMn on 2011-07-03
ubuntu-desktop installs all the graphical software you need, as well as default software that ships with ubuntu.  It's a metapackage, which means it doesn't have any content itself, but just depends on other packages.

The only partitions you can really re-use between setups would be swap (and maybe a /tmp).  Unless you have specific requirements, you shouldn't need specific partitions for "boot, swap, usr, var, tmp, opt, srv and home".  Your entire file system can be installed on one partition.  You can setup as many partitions as you want using an extended partition (they just aren't true physical partitions, which is normally OK). However, there is overhead with using partitions in that you will end up wasting drive space b/c most of them will probably never fill up, but the space won't be available to use by other folders in your directory structure.

This sounds like a lot to setup on one computer.  Unless you have to test on hardware, using virtual machines would probably be a lot easier to manage.

---

### Post by mjbrownesq on 2011-07-05
> **Rocket2DMn said:**
> ubuntu-desktop installs all the graphical software you need, as well as default software that ships with ubuntu.  It's a metapackage, which means it doesn't have any content itself, but just depends on other packages.

Thanks again for lots of feedback again Rocket2DMn; I've done some checking and I will install the server and desktop versions in the same partitions; the partitions I need (for various reasons) are:

Primary NTFS for windows
Primary NTFS for windows
Primary ext4 for /boot

Extended partition
Logical NTFS for windows
Logical NTFS for windows
Logical NTFS for windows

Then within this the normal partitions for root (/) and swap; then LVM paritions for usr, var, tmp and home.

Now I am quite confident setting up the partitions but my issue is with the booting.

I can begin with a normal full (LAMP) server install and I'm quite happy with that.  However when it comes to installing the desktop I assume I just use apt to install ubuntu-desktop.  However I assume this will then modify start up scripts and configuration to load the desktop at boot time.  This is what I need help with.

What I would like is a boot menu for Windows, Ubuntu server and Ubuntu desktop. <EDIT> I would also prefer to keep the windows boot loader rather than overwriting it.

So when I  choose server, Ubuntu will boot the same as a 'standard' server install, ie the boot sequence and running processes would be the same (similar) as another user logging into a standard server machine.  And similarly when I  choose desktop it will boot as a 'standard' desktop.

Could you (or anyone else) help me with configuring the booting?

Thanks again all.

---

### Post by drdos2006 on 2011-07-05
For your primary partitions you forgot the 100m partition for system files that Windows under version 7 requires. Plus you need another partition for /swap so your total number of partitions is five with a BIOS can only split into four primary partitions.

If you install Windows 7 make sure you install it first because it does not integrate well with linux. It overwrites any other boot system in the Master Boot Record.
Then I would install the Ubuntu Desktop with a swap space. It will see the Windows partitions and allow a grub menu for you to choose which system you want to dual boot from.
Your logical partitions can easily be set up under Ubuntu Desktop, plus you can run the server under Virtualbox at the same time as running Ubuntu Desktop.
My Virtualbox programs are as shown. With 4 Gig of RAM i could run them all at the same time if I needed to.
regards

---

### Post by mjbrownesq on 2011-07-05
> **drdos2006 said:**
> For your primary partitions you forgot the 100m partition for system files that Windows under version 7 requires. Plus you need another partition for /swap so your total number of partitions is five with a BIOS can only split into four primary partitions.
Just to clarify I'm not using Windows 7 or VirtualBox (I do actually use both for other things, but this particular post is about a setup that does not use either).

Creating the partitions is not a problem, you can create 4 primary or 3 primary and 1 extended; within the extended you can create (almost) any number of logical partitions.

For my scenario I need several windows and linux partitions, however it's not practically possible to have a boot partition withing an extended partition.  So when I make a dual boot I create a small primary partition for /boot then an extended partition for other partitions (windows and linux).

I generally let linux overwrite the MBR but I don't want that is this case; my main query as I said above is to create the boot menu with associated boot sequence and configurations for server or desktop.

Cheers.

---

### Post by mjbrownesq on 2011-07-07
Hi all

Rather than continue discussing actual installation, my main query now is the boot configuation, so I have started a new post: [http://ubuntuforums.org/showthread.php?t=1799201](http://ubuntuforums.org/showthread.php?t=1799201)

Cheers all.

---

