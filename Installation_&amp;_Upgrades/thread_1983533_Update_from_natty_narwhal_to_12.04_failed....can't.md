---
title: "Update from natty narwhal to 12.04 failed....can't reboot!"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by Nostronna on 2012-05-20
Hello,
I have a notebook dell xps m1330. Originally powerd with windows vista. With a lot of difficulties i get rid of vista and I've installed ubuntu 11 natty narwhal.
I was very happy, was working very well, but I yesterday I decided to update to the 12.04 release. I've proceeded with the normal updating procedure but during the installation of the updates, it get stuck, stop there for half a day and then the computer shut off by itself.
Now when I try to reboot it tells me

/lib/x86_64-Linux-gnu/Libc.50.6: version 'GLIBC_2.14' not found (required by /lib/libply.50.2)
General error mounting file system
A maintenance shell wll not be started

If I make ctrl D it started GRUB with a list of possibility for the reboot. I've tried all the possility, included all the recovery mode but none of them works, it goes on giving me the same error.
I've tried to make a live cd and reboot form it, but doesn't work.....the cd runs but nothing happens and it goes on with the same loop.
Anybody can help me?? Thanx

---

### Post by darkod on 2012-05-20
So, when you try the recovery mode, does it show like a menu to select what you want to do (after the language selection)? Or it doesn't even get that far?

---

### Post by ari gold on 2012-05-20
> **Nostronna said:**
> Hello,
I have a notebook dell xps m1330. Originally powerd with windows vista. With a lot of difficulties i get rid of vista and I've installed ubuntu 11 natty narwhal.
I was very happy, was working very well, but I yesterday I decided to update to the 12.04 release. I've proceeded with the normal updating procedure but during the installation of the updates, it get stuck, stop there for half a day and then the computer shut off by itself.
Now when I try to reboot it tells me

/lib/x86_64-Linux-gnu/Libc.50.6: version 'GLIBC_2.14' not found (required by /lib/libply.50.2)
General error mounting file system
A maintenance shell wll not be started

If I make ctrl D it started GRUB with a list of possibility for the reboot. I've tried all the possility, included all the recovery mode but none of them works, it goes on giving me the same error.
I've tried to make a live cd and reboot form it, but doesn't work.....the cd runs but nothing happens and it goes on with the same loop.
Anybody can help me?? Thanx
I have the same problem and I tried all different tactics of making live USB but nothing worked. I need my files.

---

### Post by ari gold on 2012-05-20
Please somebody help us out.

---

### Post by wilee-nilee on 2012-05-20
> **ari gold said:**
> Please somebody help us out.

No problem, start your own thread. :)

---

### Post by kmir on 2012-05-21
same thing here. My friend did not make a back-up of his files. How do I fix this while saving the files somehow - when I access them through a boot from a USB stick, I can't do anythign because they are 'read-only.'

---

### Post by GreatDanton on 2012-05-21
> **kmir said:**
> same thing here. My friend did not make a back-up of his files. How do I fix this while saving the files somehow - when I access them through a boot from a USB stick, I can't do anythign because they are 'read-only.'

I don't know if I understand your problem right, but maybe there is a solution in post #14.

[http://ubuntuforums.org/showthread.php?t=1980839&page=2](http://ubuntuforums.org/showthread.php?t=1980839&page=2)

Keep in mind to change the part dev/sda7 to the part where you have your operating system installed.

---

### Post by darkod on 2012-05-21
Making a live cd or live usb and booting your computer with it has nothing to do with failure of the upgrade process.

Your computer should always be able to boot from the cd or usb. And in most cases, the files on the hdd are not read-only when you are running in live mode.

Besides, read-only does allow you to copy all files to a backup location, if you never made a current backup before the upgrade.

One of the things you could try to save the installation is running fsck on the root partition from live mode. But for that you need to boot into live mode and do NOT mount the root partition. And you need to know which one is it. For example, if it's sda5, in terminal in live mode you would try:

sudo fsck /dev/sda5

Another option is entering your installation with chroot and trying:
sudo dpkg --configure -a

to try to finish the configuration of all packages that are still waiting to be configured when the upgrade got stuck.

---

### Post by Nostronna on 2012-05-21
> **darkod said:**
> So, when you try the recovery mode, does it show like a menu to select what you want to do (after the language selection)? Or it doesn't even get that far?
Hi Darko and thank you for your help.
No, it doesn't even go that far....all I can obtain is a menu of GRUB with a list of configuration to try, starting from Ubuntu with Linux 3.0.0-20 to other previous Linux version, included different recovery mode, but none of them works, they all come back to the same  point and give me the same error....
For the other solution you gave....I can't run a live cd I don't know why and I don't know what a cheroot is....sorry I'm quite new on ubuntu!

---

### Post by Nostronna on 2012-05-21
Ok, I've got a little improvement... From GRUB menu I can run "Ubuntu with Linux 3.0.9-20 generic" in recovery mode.
If I do that, it come out a "recovery menu" where I have the following options:
Resume - resume to normal boot
Clean -try to make new space
Dpkg - repair broken packages
Failsafex - run in failsafegrafic mode
Fsck - check all file system
Grub - update grub boot loader
Network - enable networking
Root - drop to root shell prompt
System summary - system summary

I've tried "resume" but doesn't work...it come back again to wthe same error.
I've tried dpkg and then reboot but no luck, same result
I've tried Failsafex but still no result

What else can I do?????

---

### Post by darkod on 2012-05-21
First select network so it can enable networking.
Then select Drop to root shell prompt.

At the prompt, try:
dpkg --configure -a

Now, since 3.0.0 is 11.10, not the latest 12.04, I am not sure it can help, but you can at least try.

---

### Post by Nostronna on 2012-05-21
I've tried also fsck and the result is the same

Mount all: /lib/x86_64-Linux- gnu/Libc.so.6: version 'GLIBC_2.14' not found ( required by /lib/libply.so.2)

There is anyway to make it found this damn file??

---

### Post by darkod on 2012-05-21
> **Nostronna said:**
> I've tried also fsck and the result is the same

Mount all: /lib/x86_64-Linux- gnu/Libc.so.6: version 'GLIBC_2.14' not found ( required by /lib/libply.so.2)

There is anyway to make it found this damn file??

Man, give us a few minutes to reply... :) Look above.

---

### Post by Nostronna on 2012-05-21
> **darkod said:**
> First select network so it can enable networking.
Then select Drop to root shell prompt.

At the prompt, try:
dpkg --configure -a

Now, since 3.0.0 is 11.10, not the latest 12.04, I am not sure it can help, but you can at least try.

Tried....if I try to enable the network it gives me this message
[428 567224] ADDRCONF (NETDEV_UP) : eth0: link is not ready

I've also tried to insert the line you told me in the root shell promp in any case (you never know...) but it said
Dpkg--configure: command not found

---

### Post by Nostronna on 2012-05-21
> **darkod said:**
> Man, give us a few minutes to reply... :) Look above.

Sorry!!! Didn't see on time!

---

### Post by darkod on 2012-05-21
Actually I'm not sure it needs the network since everything should be downloaded before the upgrade process starts.

As far as dpkg is concerned, you are running it wrong. Let me use code tags:

```
dpkg --configure -a
```

There is space between dpkg, --configure and -a, like three words.

---

### Post by Nostronna on 2012-05-21
> **darkod said:**
> Actually I'm not sure it needs the network since everything should be downloaded before the upgrade process starts.

As far as dpkg is concerned, you are running it wrong. Let me use code tags:

```
dpkg --configure -a
```

There is space between dpkg, --configure and -a, like three words.

Thank you, now I wrote it correctly but what I obtained is
Dpkg: error: unable to access dpkg status area: read- only file system

Actually on top of the recovery menu in written (file system state : read-only)

---

### Post by darkod on 2012-05-21
That was the point of Network, it would have changed it to read-write.

Try this to remount it as read write, and then the dpkg if it works:

```
mount -o remount,rw /
```

---

### Post by Nostronna on 2012-05-21
Ok, this is long....remounted and run again the dpkg, now it says

Errors encountered while processing
Module-init-tools
Libpango1.0-dev
Grub-common
Libudev0
Grub-pc-bin
Mount all
Libplymouth2
Libpango1.0-0
Libpango1.0-0:i386
Initramsf-tools-bin
Plymouth-label
Plymouth
Upstart
Init scripts
Insserv
Grub-pc
Busy box-initramsf
Friendly-recovery
Libc6:i386
Grub2-common
Initramsf-tools
Sysv-rc
Libudev0:i386

After this I've tried to reboot in any case from the recovery menu and it's still searching for this 'GLIBC_2.14' but we also have
Mount all main process (648) terminated with status 1
Plymouth-stop per-start process (652) terminated with status 1
General error mounting file systems
A maintenance shell will not be started

At go again in the same loop.....

---

### Post by darkod on 2012-05-21
Unfortunately this is not my expertize and I am running out of ideas.

It looks like the upgrade process broke off in a very bad way. At this point it might be much better to load a live session, copy any data you might need to copy from ubuntu, and do a clean install of 12.04.

Running it in live mode will also show it if it has any issues on your hardware or not.

---

### Post by Nostronna on 2012-05-21
The point is that I cannot run a drive session, not from cd nor form USB......I'll try again.
Thank you so much for all the advices!

---

### Post by darkod on 2012-05-21
That is unrelated to the hdd and the OS. You can boot from cd or usb (if you board allows usb boot) in any case, even without a hdd in the system.

That's a separate issue, either the cd/usb is not prepared correctly, the ISO image is bad, etc.

If nothing else works another option is taking out the hdd and plugging it into another machine. But you will still need to boot from cd/usb to actually make the new install.

---

### Post by Nostronna on 2012-05-22
Maybe this is not anymore the right forum....I'm trying to reboot from USB and I have now a new message...it goes so quickly that I can barely read it, hope it's written right

Un mount :/dev/: device is busy
(In some cases usefull info about process that use this device is found in isof(8) or fuser (11)
[here there is a number that I can't read on time]: stopping all devices

What that means??
Thanks...

---

### Post by darkod on 2012-05-22
That sounds like linux but on the usb. Maybe it's not created correctly or the ISO was corrupted. Try remaking it.

---

### Post by Nostronna on 2012-05-29
Finally Solved! I managed to make the live CD (was actually a problem with the image), enter in the system and save my files.
then I've reinstalled everything.
Thanks for your help!

---

### Post by SpinUp on 2012-06-10
I had the same problem after another user (*cough* wife *cough*) did a hard reset during the upgrade process.

In my case, from the root command prompt that came up by default, I ran:
```

e2fsck -C0 -p -f -v /dev/sda1

```which seemed to execute without finding errors, and then
```

mount -o remount,rw /
apt-get -f dist-upgrade

```as suggested here: [http://superuser.com/questions/420595/repair-ubuntu-after-unsuccesful-upgrading](http://superuser.com/questions/420595/repair-ubuntu-after-unsuccesful-upgrading)

Apt upgraded 1680 packages or so, and I got a few prompts to select a language and text encoding, etc., for which I accepted the defaults.  Then I was able to restart (although the restart process hung because it was blocked), and log in as usual to 12.04.  A few packages which had wanted to download data as part of the upgrade process complained, which were: nautilus-dropbox, ttf-mscorefonts-installer, and flashplugin-installer.  I reinstalled them with
```

sudo apt-get --reinstall install nautilus-dropbox ttf-mscorefonts-installer flashplugin-installer

```Right now the system seems normal, except that the package unity-scope-musicstores was kept back.  I removed that package to prevent it from bugging me since I wasn't planning to use the music store any time soon.

---

### Post by woiski on 2012-08-03
> **SpinUp said:**
> I had the same problem after another user (*cough* wife *cough*) did a hard reset during the upgrade process.

In my case, from the root command prompt that came up by default, I ran:
```

e2fsck -C0 -p -f -v /dev/sda1

```which seemed to execute without finding errors, and then
```

mount -o remount,rw /
apt-get -f dist-upgrade

```as suggested here: [http://superuser.com/questions/420595/repair-ubuntu-after-unsuccesful-upgrading](http://superuser.com/questions/420595/repair-ubuntu-after-unsuccesful-upgrading)

Apt upgraded 1680 packages or so, and I got a few prompts to select a language and text encoding, etc., for which I accepted the defaults.  Then I was able to restart (although the restart process hung because it was blocked), and log in as usual to 12.04.  A few packages which had wanted to download data as part of the upgrade process complained, which were: nautilus-dropbox, ttf-mscorefonts-installer, and flashplugin-installer.  I reinstalled them with
```

sudo apt-get --reinstall install nautilus-dropbox ttf-mscorefonts-installer flashplugin-installer

```Right now the system seems normal, except that the package unity-scope-musicstores was kept back.  I removed that package to prevent it from bugging me since I wasn't planning to use the music store any time soon.

Thank you, indeed. Your suggestions have just saved my life...
regards
woiski

---

### Post by axxs on 2013-03-28
Thank you seconded, when updating an old machine, I had the same issue occur (tho it was a housemate that pulled the plug :/ )

Your resolution saved me :) thanks again

---

### Post by Moddemeijer on 2013-04-25
In my case, it didn't work because there is no network


mount -o remount,rw /
/etc/init.d/networking start
/etc/init.d/bind9 start

Now you can try a ping, for example

ping [www.ard.de]("http://www.ard.de")

After a succesfull ping you can continue with

apt-get -f dist-upgrade

---

