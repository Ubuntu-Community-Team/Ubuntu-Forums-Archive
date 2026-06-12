---
title: "Grub Killed My Windows"
date: 2012-04-01
forum: Installation &amp; Upgrades
---

### Post by cssutto on 2012-04-01
Installed 10.4 64 bit on a new machine.

Grub killed windows.

Can not boot windows.

Any suggestions?

---

### Post by emperorpsf on 2012-04-02
commands for restore and fix windows bootloader i windows 7 from rescue cd

**bootsect /nt60 SYS /mbr **            *//this command write correct windows bootcode*


other usefull commands:

**bootrec /fixmbr **                  *//restore master boot record (not replace partition table)*

**bootrec /fixboot **                 *//write a new boot sector on system partition*

**bootrec /scasnos**

**bootrec /rebuildbcd**



this commands can fix windows bootloader but... this commands remove grub bootloader and after this operations only windows is starting.

After this operation You can re-install grub on correct partition.
Do not install grub on partition like /dev/sda1... /dev/sda2... please install on /dev/sda.
Grub automatically find all systems on HDD, if not please run "sudo update-grub".


Im not trying solution with reinstalling grub after repair windows bootloader because im not have this problem.

Im trying only restore windows bootloader with this commands and this is 100% works.

Good luck,
sorry for my bad english ;)

---

### Post by Bucky Ball on 2012-04-02
Are you getting a grub screen at boot? A list to select other kernels and OSs on the machine?

If not, try hitting escape or control after boot and that should get you the list. See if Windows is there.

Other option is to open a terminal and:

```
sudo update-grub
```Keep an eye on the output to see if it notices Windows. If so, reboot and hit escape or shift (depends on release) to get the list and see if it's there.

@emporerpsf: There is absolutely no proof yet that the Win bootloader has been corrupted. Let's see if grub's just not finding it first. If not, then maybe go that route. ;)

---

### Post by cssutto on 2012-04-02
> **Bucky Ball said:**
> Are you getting a grub screen at boot? A list to select other kernels and OSs on the machine?

If not, try hitting escape or control after boot and that should get you the list. See if Windows is there.

Other option is to open a terminal and:

```
sudo update-grub
```Keep an eye on the output to see if it notices Windows. If so, reboot and hit escape or shift (depends on release) to get the list and see if it's there.

@emporerpsf: There is absolutely no proof yet that the Win bootloader has been corrupted. Let's see if grub's just not finding it first. If not, then maybe go that route. ;)


Thanks:

This is the result.

claude@ubuntu:~$ sudo update-grub
[sudo] password for claude: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-40-generic
Found initrd image: /boot/initrd.img-2.6.32-40-generic
Found linux image: /boot/vmlinuz-2.6.32-38-generic
Found initrd image: /boot/initrd.img-2.6.32-38-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows NT/2000/XP on /dev/sdc1
Found Windows NT/2000/XP on /dev/sdc5
done

I do get the correct grub boot menu upon booting.  However I get a .....missing message.

I forget what is missing, but some windows component.

My first post was not as complete as it should have been.

I purchased a new HP with windoze 7 installed.  I downloaded and burned to a CDROM ubuntu 10.4 64 bit.

I installed ubuntu over windoze 7.  As I recall, it said something like "windows 7 has been discovered, do you want to install grub"  or words to that effect.  I don't think I was given a choice as to where to install it.

Thanks again for the help.

Edited to add that now when selecting windows from the grub menu, I get no messages; only a blank screen.

---

### Post by oldfred on 2012-04-02
Since you are showing multiple drives and installs, lets run the boot info script to see what may be missing. Since it found your Windows installs they must have the boot files. 

Have you run chkdsk on your NTFS partition from Windows repairCD?

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by cssutto on 2012-04-02
> **oldfred said:**
> Since you are showing multiple drives and installs, lets run the boot info script to see what may be missing. Since it found your Windows installs they must have the boot files. 

Have you run chkdsk on your NTFS partition from Windows repairCD?

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.


I have tried to get the machine to boot from the windows CD but it will not.

On this machine, one is supposed to press escape as soon as it starts up and that will take you to the menu from which you select the device from which you want to boot.

I get that menu, select "internal CD", the only CD choice, and all I get for it is a blank screen.

I know the CD is functioning properly as I have used it to install ubuntu as well as burning several CD's.

---

### Post by cssutto on 2012-04-02
I installed boot-repair on my hard drive and have run it several times with no success.

I am in the process of downloading the bootable CD version now.

---

### Post by cssutto on 2012-04-02
> **cssutto said:**
> I have tried to get the machine to boot from the windows CD but it will not.

On this machine, one is supposed to press escape as soon as it starts up and that will take you to the menu from which you select the device from which you want to boot.

I get that menu, select "internal CD", the only CD choice, and all I get for it is a blank screen.

I know the CD is functioning properly as I have used it to install ubuntu as well as burning several CD's.


Ran Boot Repair from the CDROM with the same results.

"Missing Device unaccessible"


The Bot Repair report is here:

[http://paste.ubuntu.com/911824/](http://paste.ubuntu.com/911824/)



When I booted I mistakenly had my Maxtor external drive turned on.  I turned it off as soon as I saw Boot Repair asking about it, thinking it would make the process shorter and easier to follow.

However, reading it, I am of the belief that I should have started over.

If you like, I will run it again.

---

### Post by oldfred on 2012-04-02
Windows 7 normally installs to two partitions a 100MB boot repair partition and the main install. I do not see a main install??

Your sda1 is the typical Windows boot partition with two of the three boot files, but the partition table says it is not NTFS, but partition boot sector - PBR says it is NTFS but has some bad data. That may be repairable, but without the main install.

Did you overwrite your main Windows install?

Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

### Post by darkod on 2012-04-02
In post #4 you said you installed over windows. It sounded on purpose.

If that is correct, what are you looking for exactly? Way to recover it?

The entry that update-grub creates is just boot files being discovered. You can't actually boot it since all of it is missing.

Although there is something really confusing in your results. First it says sda1 is ntfs with the win7 boot files, and in the fdisk part it says Linux type.

---

### Post by cssutto on 2012-04-02
> **darkod said:**
> In post #4 you said you installed over windows. It sounded on purpose.

If that is correct, what are you looking for exactly? Way to recover it?

The entry that update-grub creates is just boot files being discovered. You can't actually boot it since all of it is missing.

Although there is something really confusing in your results. First it says sda1 is ntfs with the win7 boot files, and in the fdisk part it says Linux type.

Obviously the term "over windows" did not mean over windows in the sense that windows would be destroyed.  Other wise, I would not now be trying to load windows.

I meant to convey that I installed it as per instructions on the ubunto install disk so as to have a dual boot system.

I have no idea what went wrong as I have dual boot on two other machines and I thought this would be easy.

Instead it has been a nightmare.

I am beginning to think that I will have to purchase a copy of windoze, format the entire drive and start over from scratch with a windows install followed by ubuntu.

On the other hand, I use windoze for only two things so I might just wipe this machine and reinstall ubuntu.

Best would be to save what I have if possible.

---

### Post by Bucky Ball on 2012-04-02
Save what you have to an external device and install Ubuntu sounds like a good (and easy) plan, if you don't need Windows. What are the two things you use Win for? Are there Ubuntu alternatives?

---

### Post by cssutto on 2012-04-02
Peachtree Accounting, which is not of any significance anymore as I have retired.

It would only be required if I got an audit.

The biggie is my breeding records.  They are extensive.

I have found only one linux based package that is anywhere near what I need but I have not found a way to import from the old to it.

If it were not for that, I would gladly say goodye to windoze.

I can run the breeding program on the oldest machine, but it will be awkward for reasons too long to go into here.

For now, I suspect that is what I will do.

---

### Post by cssutto on 2012-04-03
Consider this solved as I am going to format my hard drive and reinstall windows and ubuntu.

---

### Post by Bucky Ball on 2012-04-03
Then could you please mark it as 'Solved' from Thread Tools. ;)

---

### Post by cssutto on 2012-04-05
> **Bucky Ball said:**
> Save what you have to an external device and install Ubuntu sounds like a good (and easy) plan, if you don't need Windows. What are the two things you use Win for? Are there Ubuntu alternatives?


It might interest all to know that I tried several ways to get windoze to load and it would not.  The ubuntu install disk did something that windoze would not accept.

So I told gparted to make a new partition table, which gave me one ms-dos partition.

Windows liked that and installed with no hesitation or problems.

I then got the LIVE ubunto 10.4 CD and it installed easily, with very few questions asked and I ended up with the two systems installed on a neatly partitioned drive.

I would advise anyone to use the live install rather than the standard.

---

### Post by cssutto on 2012-04-06
> **Bucky Ball said:**
> Then could you please mark it as 'Solved' from Thread Tools. ;)

For some reason, there is no "SOLVED" option on my bowser.

---

### Post by cssutto on 2012-04-06
OK.

It was only solved for a couple of back and forth switches between ubuntu and windoze.

Now when I try to load windoze, I get an error and it will not load.

I have a live CD of Boot Repair and tat worked twice and now it does not work.

I suppose I need to repair grub bu all of the solutions I have seen are for the opposite problem, windoze that will not let linux load.

Somewhere I read that the ubuntu live CD will do it, but I don't get the option to repair when I fire it up.  All I get is a choice between trying it and installing it.

Any advice will be appreciated.


thanks.

By the way, I have seen enough of windoze 7 to say that they have excelled in the design of windoze 7;  that is, they have designed the worst one of all.  What a bunch of garbage to go through to get it set up.

---

### Post by darkod on 2012-04-06
If Boot Repair cd loads, create the boot info results and post the link it gives you here. We need to see more details what exactly is going on.

---

### Post by cssutto on 2012-04-06
> **darkod said:**
> If Boot Repair cd loads, create the boot info results and post the link it gives you here. We need to see more details what exactly is going on.


[http://paste.ubuntu.com/917995/](http://paste.ubuntu.com/917995/)

---

### Post by darkod on 2012-04-06
OK.

/dev/sda1 is the win7 boot partition, and the boot files are there and look correct.

However, the two boot files are also on /dev/sda2 which could create the issues you are seeing.

I would try this: Boot ubuntu, open /dev/sda2 and move the files /bootmgr and /boot/BCD to your Home folder for example.

I suggest to move them and not delete them in case you need to put them back. After that again run:
sudo update-grub

That should locate only one win7 on /dev/sda1 (because the boot files are there) and the grub2 boot menu will have only one entry for win7. Restart and try to boot win7.

---

### Post by cssutto on 2012-04-06
> **darkod said:**
> OK.

/dev/sda1 is the win7 boot partition, and the boot files are there and look correct.

However, the two boot files are also on /dev/sda2 which could create the issues you are seeing.

I would try this: Boot ubuntu, open /dev/sda2 and move the files /bootmgr and /boot/BCD to your Home folder for example.

I suggest to move them and not delete them in case you need to put them back. After that again run:
sudo update-grub

That should locate only one win7 on /dev/sda1 (because the boot files are there) and the grub2 boot menu will have only one entry for win7. Restart and try to boot win7.


I see plenty on how to edit the grub boot loader, but nothing on how to edit sda2.

How???

---

### Post by darkod on 2012-04-06
Once you boot ubuntu, open your Home folder for example (the house icon from the Unity interface on the left).

Once the file browser is opened, it will list all partitions on the left side, on the top. Just click on the partition which is sda2, you can tell by their size. It's approx 375GB. Clicking on it will mount it and open it.

Do cut-paste of those two files/folders mentioned.

---

### Post by cssutto on 2012-04-06
I removed as instructed.

Then ran Boot Repair to get this info.

[http://paste.ubuntu.com/918179/](http://paste.ubuntu.com/918179/)


Windows did not load.  Got the same error message.

---

### Post by darkod on 2012-04-06
They are still there. Look at the top, at sda2 in the Boot Files. /bootmgr and /Boot/BCD are still there. Only winload.exe should be there.

What win7 are you trying to boot, on sda1, sda2 or both?

---

### Post by cssutto on 2012-04-06
> **darkod said:**
> They are still there. Look at the top, at sda2 in the Boot Files. /bootmgr and /Boot/BCD are still there. Only winload.exe should be there.

What win7 are you trying to boot, on sda1, sda2 or both?

My mistake in not looking at it again after I moved them .  I will double check this time.

I don't remember what the windows install said, but I believe it said sda1.

I only want one copy of windows.  One of that is enough.

OK, I will have anoher go at it.

---

### Post by darkod on 2012-04-06
You do have one copy of win7. But ubuntu os-prober searches for boot files and lists all it finds. In your case you have two sets of boot files, on sda1 and sda2, so it creates two entries. I can't be sure which are the correct ones, or even if any of them will work. Maybe both sets are corrupted and you need to repair the windows boot process. Because you say the message you are getting is from windows. Grub2 is just trying to boot it, it's not responsible for what happens later.

---

### Post by cssutto on 2012-04-06
Well, it took a long time to go through all of the steps, but the bottom line is the problem is cured.

I first determined that the items moved where where I thought the were.

Then I went back into sda2 and sent the items not needed to the trash.

So then I tried to boot windoze and it failed.  Of course, it offered to fix the problem and I allowed myself to be sucked in.

Talk about watching paint dry.

That little blue thing went back and forth 1,000 times.  It must have gone on for 20 minutes.

And then came up failed.

Bill Gates may have assembled the world's greatest sales team, but his programmers have to be the world's worst.

So then I loaded Boot Repair and let it do its thing.

I then tried to load windoze and it worked!!

Folled with it a few minutes to give it time and then closed it and reloaded it again and it loaded just fine, so it must be fixed.

I do appreciate the help.  Never would have had the smarts to figure it out myself.

Thank you.

---

### Post by Bucky Ball on 2012-04-07
Excellent. 'Solved' is not in your browser. If you click 'Thread Tools' at the right above the first post on this page you will find 'Solved' on the drop-down list. Select it. That's it. ;)

---

### Post by cssutto on 2012-04-09
> **darkod said:**
> If Boot Repair cd loads, create the boot info results and post the link it gives you here. We need to see more details what exactly is going on.


Thanks.

But now it is not completely solved after all.

When I reinstalled everything, I took a quick look at windoze and it looked OK.

So I closed it and went back to ubuntu which is much more important to me.

When I got the chance to go back to windoze, I found that windoze does not see my USB or Ethernet ports.

I have seen advice that one should go to hardware manager to track down the problem.  I have had many different versions of windoze with the last two being 2000 Professional and XP and yes they had hardware managers.

I do not find it in windoze 7.

So I looked at doing a repair with the installation disk but lost my nerve because MicroSoft likes to have no competition and I am not sure that it will not destroy Ubuntu in the process even though it says that it will not change any of the data files.

That might mean that it will change only windoze 7 system files and it might not.

If anyone knows for certain, I would appreciate comments.

I have put too much into getting Ubuntu set up on this machine to start over.

---

### Post by cssutto on 2012-04-09
OK, I finally found it.

Congratulations to windoze.  They have managed the impossible.  They have made windoze even less intuitive than it has been.


But now the problem is that the drivers are not loaded.  Drivers are not to be found on my installation nor are they to be found on the windoze installation disk for which I paid a big price.

They instruct me to go on the internet and find them.

Great.  Now how do I do that with no ethernet connection to my router and no USB for my cell.

I suspect that the wireless driver is also not installed.  I forgot to look at that.

I have another ubuntu machine here and can burn a CDROM on it but I don't know what driver to purchase for this machine.

So I will have to dig that info up the hard way.

So consider this problem solved.

---

