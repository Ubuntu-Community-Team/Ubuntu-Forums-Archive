---
title: "update-initramfs leads to getopt: 1: Syntax error"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by Eyjafjallajoekull on 2010-04-17
Hi all,

I've been happily using Hardy for nearly two years as a relative noob. But a recent update on time zone data (tzdata) seemed to coincide with a persistent failure notice whenever I attempted updates using synaptic:

[COLOR=Green]linux-image-2.6.24-27-generic: subprocess post-installation script returned error exit status 2[/COLOR]

The details of the error are revealed in a *terminal* style window by the synaptic GUI and this is what is included in that report:

```
Setting up linux-image-2.6.24-27-generic (2.6.24-27.68) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-27-generic
/usr/bin/getopt: 1: Syntax error: ")" unexpected
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.24-27-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-27-generic (--configure):
 subprocess post-installation script returned error exit status 2
```I've spent some time searching the forum posts for help. I downloaded a new copy of *getopt* and put it in /usr/bin after reading one thread. I then did 

```
sudo dpkg --configure -a
```This produced the following:

[COLOR=Green]Setting up samba-common (3.0.28a-1ubuntu4.11) ...
/usr/bin/ucf: line 338: /usr/bin/getopt: cannot execute binary file
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 3.0.28a-1ubuntu4.11); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured[/COLOR]

...which then led into a repeat of the error lines above and a whole lot of other stuff (I assume caused by dependency problems).

The thread I was looking at also had the suggestion of running:

```
sudo aptitude update

```...so I did that and fetched 62.0kB. I then typed (as per this thread I was following):

```
sudo aptitude safe-upgrade
```...which (after typing y to continue), gave me:

[COLOR=Green]Removing linux-headers-2.6.24-19 ...
Setting up linux-image-2.6.24-27-generic (2.6.24-27.68) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-27-generic
/usr/bin/getopt: 1: Syntax error: ")" unexpected
Terminating...[/COLOR]

...and so on (ie, back to square one).

I'm grateful for any advice anyone can give as to how I can get my sense of inner peace back. I'm not an ubuntu geek, but I'm happy to read links if you can point me in the direction of anything useful. I haven't found what I need so far - hence my first post.

E :)

ETA - that loose smiley some 9 nines up in the green is obviously meant to be a *8* followed by a *)*
Pesky things...!

---

### Post by quixote on 2010-04-19
Just a wild guess, but since you didn't do anything non-standard the first time, the reason it didn't work was probably a bad download.  Either the file itself was corrupted or it became that way travelling to your computer.

Can you boot into one of your earlier kernels at the grub menu?  Instead of going with the default, use the down arrow key to get to an earlier version (not one of the recovery modes).

If that works, use it for a week or two and try again.  If it was a bad file, one would hope they'd fixed it by then!

If that doesn't work, then plug an ethernet cable into your computer, and boot into a recovery mode, selecting "root with net access" for a boot option.  Once you have the command prompt (remember, you're root, so don't make any typos!) run the following:```
dpkg --configure -a
apt-get -f install
apt-get update
```

If that still doesn't work, let us know what new error messages you're getting.  (Hopefully, at least the errors will change!)

(To beat back the smileys, use CODE tags, the # up in the formatting bar:```
8)
```8) )

---

### Post by Eyjafjallajoekull on 2010-04-21
Thanks for your reply quixote. I may have given the impression I knew a bit more than I do...

I've looked around at what *grub* is/does (I've never come across it before and have not knowingly installed it up to now).

So [this thread]("http://ubuntuforums.org/showthread.php?t=1014708") seems to cover how to (re)install *grub*. Is that the thing for me to do, to see if I can boot into an earlier kernel? Is it too late to think about using *grub* if I haven't done so before? I'm Hardy, so will follow the legacy *grub* instructions if grub's the thing to do.

The second suggestion you make has left me totally confused (pretty easy to do, I'll admit). I've got an ethernet cable in here just now since my router is linked to two PCs via a hub (the other PC is running winXP). How does having the cable in there help in booting differently? Are you assuming I might have another linux box around?

Anyway, if the grub thing is the way to go, that last one won't be an important question.

Thanks again for your time.

E

---

### Post by Eyjafjallajoekull on 2010-04-21
Ok, how much do I wish I'd tried that first...?

I just rebooted and spotted the *grub* menu option and Esc'd into it (never paid it any mind before...).

Anyway, I did what I remembered you'd said. I chose an earlier kernel - 2.6.24-26  (& not a recovery mode). All seems ok, boots up fine. But there's an update notification. So I do the synaptic update manager and see that I'm looking at 4 *important security updates*. They are listed below. I keep them all checked and go ahead with the update. At the end, I get a pop-up with the following:
```
E: linux-image-2.6.24-27-generic: subprocess post-installation script returned error exit status 2
E: samba-common: subprocess post-installation script returned error exit status 126
E: samba: dependency problems - leaving unconfigured
E: smbclient: dependency problems - leaving unconfigured
E: libpam-smbpass: dependency problems - leaving unconfigured
```...and in the detail report that follows, I can see the exact same lines I quoted in my OP:
```
[COLOR=Green][COLOR=Black]Setting up linux-image-2.6.24-27-generic (2.6.24-27.68) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-27-generic
/usr/bin/getopt: 1: Syntax error: ")" unexpected
Terminating..[/COLOR].[/COLOR]
```So did I make a noob boob? Is that expected, given what I did? It doesn't seem to have improved any.

Thanks in advance,

E

Update packages:
libavcodec1d
libavformat1d
libavutil1d
libpostproc1d
  (ie, all mpeg stuff)

---

### Post by Eyjafjallajoekull on 2010-04-21
So after making the last post, I notice there's no update notification up in the top right of my GUI. I wonder whether the problem has resolved. I decide to reboot. At this point I realise I have no idea whether the *grub* menu is something I need to use on each boot to get the earlier kernel. I figure I'll let it do its own thing and see what happens. Again, boots up fine. No red update icon nagging at me up there. Wonders... can I tell which kernel is being used? So I hunt around the system menu and find that *system monitor* handily shows me I'm using Kernel Linux 2.6.24-27, which is not the earlier version I chose last time - it's defaulted to the later one. But, hey, there's still no update notification! Does that mean the problem's solved?

I guess I'll post here in a coupla days and report what it's telling me...

Thanks again,

E

---

### Post by quixote on 2010-04-22
Sorry for whizzing along at light speed.  Taking it a bit slower... Grub is a bootloader, which means it's a tiny bit of code that tells the machine how to boot.  It's independent of the operating system, so I'm not sure you have to use grub-legacy with Hardy.  Grub-legacy is easier to configure (for me, anyway, because I'm used to it), but less robust and flexible than grub2.  One of the two comes with every install of ubuntu.  You don't need to, but can, install it afterwards yourself.  For instance, to go from grub-old to grub2, or vice versa.

If you boot into an older kernel, it's not exactly like using a "System Restore Point" in Windows, but it's kind of the same idea.  Updates to the kernel are in the newer option.  Since they're not in the earlier option, you'll get the same update notice as you started with.  And when you've pushed the button and updated, well, then the system doesn't have anything to complain about. :)

Grub, unless you tell it otherwise, boots into the first option by default, which will be the newest kernel.

If, at this point, things are booting okay, don't worry about warning messages.  If it doesn't boot, it needs fixing.  If it merely complains, usually you don't have to worry about it if the system runs normally.  Those messages mean something to people who know what they're doing, but for the rest of us ... not so much.  

About booting into "recovery mode" with an ethernet cable attached: if you select that option, you get six choices about how to boot.  The last one is "root console with network access" or something like that.  If you're trying to fix a broken system from the command line you need to be able to download the fixes, so that's why the ethernet.  Luckily, you don't need to worry about that, since your system seems to be working.

---

