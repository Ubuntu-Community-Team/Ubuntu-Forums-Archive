---
title: "Dual processor"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by stevesmith on 2006-08-29
Hi all

I'm trying to boot a Dapper disc as a live CD on a dual PIII 800
Compaq ProLiant ML350.  It throws up:

[4294669.909000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC

If I boot with notsc it gets past that and after "Configuring some
drivers..." for some time it lands me at a screen with nothing but a
blinking cursor and that's as far as it gets.  Anyone know how to get
it going?

Steve :)
[https://wiki.ubuntu.com/SteveSmith](https://wiki.ubuntu.com/SteveSmith)

---

### Post by DarthMandeep on 2006-08-29
I'd try booting with the "noapic" option also. I'm not sure it will fix this, but given the message, it's worth a try.

---

### Post by stevesmith on 2006-08-30
Thanks!  That got a bit further, now I get a desktop with blank top panel after a long wait.  I've filed a report at:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/58255](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/58255)

---

### Post by mikecindi on 2006-09-08
Steve,
I also have a ProLiant ML350 dual PIII. I was able to use the liveCD (6.06) as follows:
On the initial liveCD boot append
**pci=noapic**
to the boot line. I found this in the help by pressing F1 and then F8.
Then run the installer once OS is up.
On the reboot when the appropriate GRUB message appears press
**esc**
and highlight the following menu entry (which should be the default):
**Ubuntu, kernel 2.6.15-23-386**
and press
**e**.
On the next screen highlight the line that contains the kernel statement which should be something like this:
**kernel  /boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet splash**
and press
**e**
and append
**noapic**
to that command line. Press
**enter**
to return to the previous screen and then press
**b**
to boot. Once you the OS is loaded you will need to edit the GRUB menu list (unless you want to append the **noapic** option every time you boot your machine). Open a terminal and at the prompt type:
**sudo gedit /boot/grub/menu.lst**
you will be asked for your password (not the root password which does not exist unless you set up the root account). When *gedit* opens you will probably have to scroll past a lot of commented-out statements to get to the actual statements for your setup. Append the **noapic** to the  command line *# defoptions=*. I also added it to the *# altoptions=(recovery mode)* statement. Save the file, close *gedit* and then you need to update GRUB by running
**sudo update-grub**
at the command prompt.
I hope I've not been too simplistic in my instructions and hope that you get things up and running soon now.
Mike

---

### Post by stevesmith on 2006-09-16
Thanks for that!  I've afraid I haven't been on the forum for a while and didn't see your post in time.  Today I managed to get it going with the alternate (text install) disc.  If I need to use the live cd on it again, I'll give your instructions a go.

Thanks again!
Steve

---

### Post by qhartman on 2007-04-02
Just a quick note that as of today, April 2  2007, if you switch to the "server" kernel after the initial installation everything works just fine without any oddball kernel boot options.

---

