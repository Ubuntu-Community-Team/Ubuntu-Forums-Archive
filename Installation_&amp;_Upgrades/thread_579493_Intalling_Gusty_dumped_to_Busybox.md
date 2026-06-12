---
title: "Intalling Gusty: dumped to Busybox"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Thomas-nll on 2007-10-18
I tried to run/install the new Gusty release from the live-cd, but I don't even get to the installation phase. 

After the boot menu of the live-cd, I get dumped in Busybox (whatever that may be). The same happens when I select safe mode.

Just prior to the boot menu, I briefly see some kind of error messages stating "cannot allocate resource [...] region [...]" or something like that (it disappears really quick, so I'm not really sure).

I use a Acer Travelmate 8100 laptop (ati X700, Pentium M, 1GB mem)

Does anybody know a solution?

---

### Post by Separ on 2007-10-18
Try the alternate CD, that's what I'm having to do, if it works, I'll give you an update.

---

### Post by csmth on 2007-10-18
I face the same problem, but I can't run the liveCD (because monitor "Out of range", God damn the 1280x1024 mode).

I install with alternative CD, and it truns into the busybox at the system restart.

---

### Post by rotk on 2007-10-18
I too have that problem. I thought it must have been fixed by now :(
I used to get it when running Feisty (amd64 + amd64 alternate)

---

### Post by rotk on 2007-10-19
bump

---

### Post by rotk on 2007-10-19
Can some one help us in this!!

system is amd64 
install image = ubuntu-amd64 on a dvd

cat casper.log says
unable to read /dev/fd0 (why is it reading floppy?)

tried inserting some random floppy, it says can't read IO Error!

also tried adding "acpi=off all_generic_ide" to boot options but didn't work (previous fiesty fixes)

---

### Post by rotk on 2007-10-19
my casper.log says

```
 /init: /init: 1: cannot open /dev/fd0: no such device or address
stdin: error 0
stdin: error 0
stdin: error 0
Unable to find a medium containing a live file system

```

---

### Post by Thomas-nll on 2007-10-19
Where can I find these log files?

---

### Post by zalo on 2007-10-19
If the Desktop CD doesn't work then try the Alternate CD.

Don't waste your time trying to get the Desktop CD working.

---

### Post by T_Jonsson on 2007-10-19
uppgraded with the upgrade manager and at restart of the system i get the message 
"udevd-event[2154]: run_program: '/sbin/modprobe' abnormal exit". 

And then i'min BusyBox.

---

### Post by Crashedfiesta on 2007-10-19
> **rotk said:**
> Can some one help us in this!!

system is amd64 
install image = ubuntu-amd64 on a dvd

cat casper.log says
unable to read /dev/fd0 (why is it reading floppy?)

tried inserting some random floppy, it says can't read IO Error!

also tried adding "acpi=off all_generic_ide" to boot options but didn't work (previous fiesty fixes)

This is exactly the problem that I have.  My system is a rather old AMD XP1500+ but it's worked fine with 6.06 previously.  I'll give the alternate CD a go...

---

### Post by rotk on 2007-10-20
Thomas-nll

In the BusyBox shell. You will have few useful commands available during install. 
casper.log is in it's root directory.
Or you can press F6 and modify the boot options, removing quiet and splash, thereby you could see what's going on in text mode. 

Crashedfiesta

Please tell me if the alternate cd works.

---

### Post by Crashedfiesta on 2007-10-20
> **rotk said:**
> 

Crashedfiesta

Please tell me if the alternate cd works.

Nope. I get the same problem but after disabling the FDD controller in BIOS it gets stuck when looking at the USB hub.

---

### Post by dotman on 2007-10-20
This may or may not be helpful, but I was having the same problem when I realized that it looked as though my computer was trying to access my *other* CD drive which happens to be the master on my primary IDE bus. This drive has caused me problems in the past but I have been too lazy to simply unplug the thing, so continuing my streak of laziness I ejected the drive's tray (and kept it ejected) during the start up of the live session and it worked.

This may not have any relevancy to your guys' problems, but I figured I'd post my results just in case someone, somewhere had the exact same problem as me.

---

### Post by fireworksshow on 2007-10-24
Same problem as the others dumbed to busybox '/sbin/modprobe' abnormal exit.
Hasn't anyone managed to find a workaround?

---

### Post by Sam C on 2007-10-24
I've had the exact same problem
I had Edubuntu 7.04, and wanted a clean install

The Ubuntu 7.10 Live CD would always go to the Busybox thing, with "(initramfs)" written below, and then lost of other numbers and letters that made no sense

Then, I downloaded the alternate CD. Everything worked out, up to booting it up for the first time. It froze on the screen with just "Ubuntu" and a progress bar, and then, back into Busybox.

The same thing happened to recovery mode, and when booting up XP all the files seem to be there.

The messages Busybox gives include:
> 
[  188.420000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
and
> [  249.168000] sd 2:0:0:0: [sdc] Assuming drive cache: write through

I also upgraded my laptop from Edubuntu 7.04 to 7.10 through the update manager with no problems

I should also mention my computer
AMD 1200Mhz, not 64 bit
512 mb RAM
20 and 40GB hard drives (IDE)
nVidia geforce, not too sure what but old enough
no-name motherboard, again I don't know who made it

Thanks,
Sam

---

### Post by tajreed on 2007-10-24
My prob also:

It seems as if many folks are having trouble installing via the live CD and booting to 7.1 from an upgrade. The UDEV event error seeming to be the most popular. I have the same problem. I upgraded to 7.1 from Feisty but could not boot to the 2.6.22.14 kernel and instead am using 2.6.22-12. I get the Udev error when trying -14. 7.1 works perfectly for me with the -12 kernel.

Same situation when trying to re-install via the Live CD. Same error. I assume that Live CD starts with the -14 kernel. Hence, the same error.

Has anyone figured this problem out?

---

### Post by Sam C on 2007-10-26
bump

---

### Post by xyphur on 2007-10-29
...this issue apparently had a fix for some people under Feisty, by adding 'break=top' to the LiveCD's F6 boot line, getting dumped to the BusyBox prompt, doing a 'modprobe piix' then 'exit' and it would supposedly boot normally after that... Such is not the case with Gutsy, as that module isn't found when trying to probe it... at least not from the LiveCD.

So, bump. Let's get this solved already.

---

### Post by Digitalfilm43 on 2007-10-30
I'm having the same problem as well.  I upgraded to 7.10 from 7.04 by way of the update manager and after restart, it froze at the Ubuntu screen with progress bar, then eventually dumped me into the busybox shell.  That happened while loading from the default kernel 2.6.22-14.  It loads fine from the 2.6.20-16 kernel so I've made that the default and everything seems to work.

AMD 1700 (1100 mhz?) not 64 bit
Nvidea Geoforce FX3200
ECS KS75A motherboard
384 mb RAM
80 gig IDE HD

---

### Post by tajreed on 2007-10-30
Problem continues without apparent fix. Same here., I have to use the -12 kernel as default. -14 in Gutsy will not boot. And I cannot reinstall via the live CD because of the Busybox error. I've tried different downloads of the Live CD, different burn speeds, the Alt. CD, cleaned the head on the CD, fiddled with the bios and other things. To no avail.

The only thing that I can see is that Gutsy -12 kernel sees the drives as hda whereas on  my other machine Gutsy labels the drives as sda and I use the -14 kernel.

---

### Post by Sam C on 2007-11-02
bump

---

### Post by nikef on 2007-11-07
Any fix to this problem yet?
i am getting the same error  :confused:

---

### Post by andrewheiss on 2007-11-10
I'm having the same problem, trying to install Edubuntu 7.10 on a P4 IBM laptop. If I boot from the CD with the floppy disk enabled in the BIOS, it hangs at i/o error on hd0 or whatever that error is. If I disable the floppy, it dumps me to Busybox, which is kind of lame. Any fix on this yet?

---

### Post by sharmaravi on 2007-11-15
I had the same problem and found a workaround on launchpad. System boots fine after adding kernel option 'all_generic_ide'. This is what I have in menu.lst

kernel /vmlinuz-2.6.22-14-386 root=UUID=... ro quiet splash all_generic_ide

Here is the launchpad link

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/154591](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/154591)

Someone also found the problem in kernel and posted a fix on launchpad. Here is the link

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156428](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156428)

Seems the problem is associated with Seagate drives, the link above list two models : ST340823A and ST320413A. I have ST320413A as a second drive in my system.

Hope this workaround helps you guys too.

---

### Post by holvoetn on 2007-11-19
sharmaravi, you're a STAR ! :):KS

Adding all_generic_ide made my system boot into LiveCD !
And no, I do not have any Seagate disks (am installing to system only having USB-HDD but unable to boot from USB).

---

### Post by blackest_knight on 2007-12-20
Similar issues here feisty was able to slowly boot but adding all_generic_ide to the startup means much quicker boot times and faster disk access. 

i am in the process of upgrading to gutsy and hope i can get past busybox if i ensure i edit menu.lst before rebooting. 

my issue is with a seagate drive the smaller of the two listed. 

I'm part way through turning an old time computers pc into a reasonable PC seems the only thing I havent upgraded is the case and mainboard. try running 3 hds and a cd burner with a 145 watt psu!

If the IDE option doesnt work for gutsy i think i will need to build a patched kernel. This will be a learning experience. :)

---

### Post by jaiagreen on 2008-01-01
I tried the "all-generic-ide" option and STILL get dumped to BusyBox. (Yes, I do have a Seagate hard drive.) I also us "noapic" to get around another problem, but get dumped whether I enter that or not.

---

### Post by Alef Auman on 2008-01-07
BusyBox v1.1.3 (initramfs) 

--------------------------------------------------------------------------------

When I try to install mythbuntu 7.10 I get the following message:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

I've found an interesting link which is maybe also my problem:
[https://bugs.launchpad.net/ubuntu/+s...22/+bug/156428](https://bugs.launchpad.net/ubuntu/+s...22/+bug/156428)

I'm using also a seagate harddisk ST320413A.

Is it possible to get a new iso file for this or can you explain me step by step how to do this?

When hitting Ctrl+Alt+F4 I get the following message:
cp : unable to open /root/var/log: No such file or directory
mount: mounting /root/dev on /dev/.static/dev failed: No such file or directory
...
...
target filesystem doesn't have /sbin/init

---

### Post by MCube78 on 2008-02-01
> **Alef Auman said:**
> BusyBox v1.1.3 (initramfs) 

--------------------------------------------------------------------------------

When I try to install mythbuntu 7.10 I get the following message:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

I've found an interesting link which is maybe also my problem:
[https://bugs.launchpad.net/ubuntu/+s...22/+bug/156428](https://bugs.launchpad.net/ubuntu/+s...22/+bug/156428)

I'm using also a seagate harddisk ST320413A.

Is it possible to get a new iso file for this or can you explain me step by step how to do this?

When hitting Ctrl+Alt+F4 I get the following message:
cp : unable to open /root/var/log: No such file or directory
mount: mounting /root/dev on /dev/.static/dev failed: No such file or directory
...
...
target filesystem doesn't have /sbin/init


I have the very same problem. As I insert the Live CD 7.10 it seems to load then I'm just dumped to BusyBox with no error message at all.

I'm runing and XPS M1210 dual core etc..

suggestions please?

 cheers

MCube

---

### Post by DanaKil on 2008-02-07
I have a related bug since Feisty I think but I encounter this problem only from times to times (but quite frequently). So sometimes, I have to reboot 6 or 7 times because I remain stuck at the ubuntu splash screen (Kubuntu actually). 
When I wait a (sometimes very long) time, I have the busybox/initramfs screen. I've seen others users with a similar problem.

note: this is not a problem with a live CD but with my current install
 
I have an intel dual core with 2 HD (Samsung and Hitachi). The samsung one is a SATA drive. My DVD burner is also a SATA one. My kernel is 2.6.22-14-generic.

It's difficult to test boot options because the problem don't appears at each boot (and never append when I want actually...)

Thanks for any additional informations :)

---

### Post by amtur_poet on 2008-05-14
When I tried it, it just automatically went to busybox with no visible error messages. This problem was fixed in hardy, right?

---

### Post by EXCiD3 on 2008-05-14
> **amtur_poet said:**
> When I tried it, it just automatically went to busybox with no visible error messages. This problem was fixed in hardy, right?

You can try the "all_generic_ide" boot parameter (Press F6 at the GRUB menu and add it to the boot line). This hopefully was fixed in Hardy, just download an iso and try it out!

---

### Post by amtur_poet on 2008-05-15
Do you mean just adding the words "all_generic_ide" to the boot parameter? I tried that and it still went to busybox. Also, I am using a customized live CD.

---

### Post by DanaKil on 2008-05-15
> **EXCiD3 said:**
> You can try the "all_generic_ide" boot parameter (Press F6 at the GRUB menu and add it to the boot line). This hopefully was fixed in Hardy, just download an iso and try it out!

The "all_generic_ide" resolve indeed all my problem (my ubuntu boot fast and without any problems). This solution worked on gutsy and now, in Hardy (so it's not fixed but the workaround is still functionnal)

Cheers

---

### Post by EXCiD3 on 2008-05-15
> **amtur_poet said:**
> Do you mean just adding the words "all_generic_ide" to the boot parameter? I tried that and it still went to busybox. Also, I am using a customized live CD.

There are multiple reasons for a drop to busybox and this fixes only a few. Unfortunately there isnt too much information given about the cause for this. Works for some, not others.

---

### Post by 52rockwell on 2008-05-17
I have had  this problem on my Dell Inspiron(sure)530. I read through the thread and I tried changing my harddrive to RAID in the bios as my first fix ..IT Worked.
Man, I have run Ubuntu on all my old laptops with no speed or power. It is really nice to use it on a newer machine. 
 I think Ill be using it alot more for all my web browsing and fun stuff.

---

### Post by dwolfggc on 2008-06-22
I just had a problem with being dumped to busy box with a 8.04 live CD. It wouldn't boot or install. I unplugged the floppy drive and it worked fine. I looked all over for an answer for this and finally just started unplugging stuff. I read somewhere that it has to do with driver issues. So if anyone has this problem I suggest trying the simplest hardware configuration you can get (No floppy, extra cd-rom, card reader, video card if you have one onboard, ect.) thats what fixed it for me.

---

