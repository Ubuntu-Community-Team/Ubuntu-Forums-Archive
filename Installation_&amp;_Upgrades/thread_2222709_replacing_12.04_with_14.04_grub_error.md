---
title: "replacing 12.04 with 14.04 grub error"
date: 2014-05-07
forum: Installation &amp; Upgrades
---

### Post by s9032g@comcast.net on 2014-05-07
From an iso I replaced 12.04 with 14.04. Upon doing the suggested restart I got an error message 

Grub Loading
error file not found.
grub rescue>

After seeing this I reloaded  14.04 and after restart I got the same message.

Help Please!

---

### Post by Bashing-om on 2014-05-07
[email]s9032g@comcast.net[/email]; Hi !

1st and:
Off Topic: You may not want your email address public - web crawlers !!- suggest ya get with the moderators and get a "normal" username established !

To the issue at hand:
Maybe not  big deal to fix.
Show what we are working with.
From the liveDVD -> "try ubuntu" mode -> desktop -> key combo ctl+alt+t to get a terminal interface.
In this terminal execute the terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
and post the outputs - between code tags - ;
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

The outputs will give the file system(s) partitioning information such that we know where and how to install grub (GRand Unified Bootloader) to.
If it ain't UEFI in control of the boot process, then
[INDENT][INDENT][INDENT]it ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2014-05-07
+1 on bashing-om's suggestion of a name change. Only admins can do that. 
Please post in Resolution center. And read sticky on name changes. PM required to prove you are you or something.
[http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)
Offer three options for Admin to change you to.

---

### Post by s9032g@comcast.net on 2014-05-07
What you see is not my real address. Thanks anyway.

Will try your suggestion.

---

### Post by Bashing-om on 2014-05-07
[email]s9032g@comcast.net[/email]; OK ,

Waiting on the requested outputs to advise how to (re-)install the boot manager.

[INDENT]ain't nothing but a thing
[/INDENT]

---

### Post by s9032g@comcast.net on 2014-05-08
Bashing-Om

Before I try your suggestion let me get it straight:  You said:

From the liveDVD -> "try ubuntu" mode -> desktop -> key combo ctl+alt+t to get a terminal interface.
In this terminal execute the terminal commands:

So I should boot again using the 14.04 iso DVD? Somewhere at the start there is a place to select "try Ubuntu. (note that nothing but Ubuntu has ever been on this laptop starting with 8.04). Then to "desktop", hit the keys you gave me, get a terminal interface, and proceed with the commands. RIGHT?

I also have a "boot repair iso". Is that of any use?

As you can see I am not a tech wiz.

Thanks

---

### Post by Bashing-om on 2014-05-08
[email]s9032g@comcast.net[/email]; Hey,

Yes you have the procedure correct.
Mind you this is but a precursor to make sure of where/how to install ubuntu's boot manager.

In respect to:
> 
I also have a "boot repair iso". Is that of any use?

Perhaps of value to you;
IF the "boot repair .iso" is our boot-repair (YannUbuntu's);
IF you are the more comfortable following a GUI install;
IF there is but the one physical hard disk installed in your machine (else you need to pay close attention to what you are doing);
Then, yes, boot-repair is a great tool to automate the installation of the boot manager, as we are proceeding to do manually.

Off topic:
Being cautious is a good thing, being fully aware of what is being done is a good thing, learning the operating system is a good thing.
Not knowing is not a sin, none of us were born knowing what we know. -> our purpose here is to help in general, getting you the boot manager installed in this instance in particular.

Back on topic:
Now IF and a big IF, the results of the requested commands come back that your partitioning is the legacy msdos (NOT MicroSoft at all ) type AND there is but the one hard disk installed, AND 'root' is installed to the partition sda1, then the commands to properly install ubuntu's boot manager will be:
From the liveDVD - same version as what is installed onto the hard drive - -> terminal ->
terminal commands:
```

sudo mkdir /mnt
sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```
The boot manager is now installed to the hard drive.
Reboot and re-set in bios the boot priority to boot from the hard drive
And in termianl, check and verify that there are no errors reported.
terminal commands:
```

sudo grub-install --recheck /dev/sda
sudo update-grub

```
As there are no errors reported, all done -> happy happy ubuntu'n !

BUT, to make sure what is the most likely, show us what the partitioning is like, provide the outputs of the terminal commands from the liveDVD of 'fdisk' and 'parted'.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by s9032g@comcast.net on 2014-05-08
There is only one hard disc. The laptop is a Dell and it came with Ubuntu installed by Dell. Whatever partitioning is present is whatever Dell did, as I have never changed anything. I have always done a clean install when moving to the latest Ubuntu version. After 12.04 LTS came out I stuck with it until 14.04 LTS came along. Using my DVD iso I did select "upgrade from 12.04". Perhaps I should have done a clean install again???

Does this sound like it meets the criteria you so nicely laid out to solve my problem? I am guessing yes.

Might I be better off to just do  clean install?

Thanks for the help. Ubuntu and its people are the best.

---

### Post by Bashing-om on 2014-05-08
[email]s9032g@comcast.net[/email];

Simple, should be straight forward, run the terminal commands to (re-)install the boot manager.
Else if you want confirmation as the the hard disk, by all means feel free to post the original request.
The online version "upgrade" works great in most cases, not disabling some 3rd party PPAs in some circumstances causes problems.
If ya want we can, after the booting issue is resolved, run some terminal commands to insure the upgrade is complete. 

As presently all we are looking at is a booting issue, I see no need to consider - at this time - a clean (RE-)install.

[INDENT][INDENT]as we go
[INDENT][INDENT][INDENT]merrily on the way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by NoDeity on 2014-05-08
I had the same problem after using a "live" DVD to update my 12.04 to 14.04.  I followed the "boot-repair" instructions on this page and it fixed me right up: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I used the 2nd option, "install Boot-Repair in Ubuntu".

---

### Post by s9032g@comcast.net on 2014-05-09
Thanks Bashing-Om and No Deity.

I will give it a try. I always like to hear that someone has actually done this and had it work! In the past I have had some poor results with advice based only on a hypothetical.

---

### Post by s9032g@comcast.net on 2014-05-09
:) I am now responding using my repaired Ubuntu 14.04 LTS installation. 

Thanks folks for getting this fixes!

Since I had already burned the Boot Repair iso (referred to earlier in this thread) I decided to use the first option, whereas NoDiety opted for option 2. In using the repair disc I avoided typing in all those terminal commands and having the program reside on my hard drive. It was simple and fast. As I watched the details I could see that it dealt with Grub almost entirely.

As part of the process it also created a URL report about the boot and gave me a link to that report which I could then (if necessary) post on this thread (as suggested by Bashing-om.

All is well. What a great forum!

---

### Post by Bashing-om on 2014-05-09
[email]s9032g@comcast: Outstanding !

You do good work .

See there, it was
[INDENT][INDENT]nothing but a thing
[/INDENT][/INDENT]

---

### Post by NoDeity on 2014-05-10
Nice.  :-)

---

