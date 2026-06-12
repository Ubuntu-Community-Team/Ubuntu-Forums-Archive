---
title: "Problem with booting and loading Ubuntu"
date: 2006-07-16
forum: Installation &amp; Upgrades
---

### Post by AhrenBa on 2006-07-16
Hello,
I have been trying to boot and later install the ubuntu cd. However it gets to a point where it keeps displaying:

"Buffer I/O error on device hdc, logical block 0"
THEN
"Buffer I/O error on device hdc, logical block 1"
THEN
"Buffer I/O error on device hdc, logical block 3"

and so on.......

It keeps doing this forever and won't let me get past this point.

Why is it doing this and how can I fix this? I really want to install Ubuntu.

---

### Post by Choad on 2006-07-16
<random guess>
unplug all cables from the hard disk and blow the dust off and reattatch.

alternatively remove the offending hard disk all together temporarily and see if it will boot
</random guess>

---

### Post by cotcot on 2006-07-16
or try the Alternate installCD

---

### Post by AhrenBa on 2006-07-16
Thanks for the suggestions guys. I think the reason why it is not working is because I completely forgot about something when trying to boot. Ubuntu needs at least 192MB of RAM and the old computer I was trying to install it on has only 160MB. Humph....

Anyways, can any of you recommend a good distro that will run on a machine with 500mhz celeron processor, 160mb RAM, and 4GB hard drive? Thanks.

---

### Post by Choad on 2006-07-16
> **AhrenBa said:**
> Thanks for the suggestions guys. I think the reason why it is not working is because I completely forgot about something when trying to boot. Ubuntu needs at least 192MB of RAM and the old computer I was trying to install it on has only 160MB. Humph....

Anyways, can any of you recommend a good distro that will run on a machine with 500mhz celeron processor, 160mb RAM, and 4GB hard drive? Thanks.
yep, xubuntu

its truly awesome, xfce has come a long way in the past year

---

### Post by blackest_knight on 2006-07-16
I just installed xubuntu on a p166 with 48 meg of ram its net connected and using wireless.  
is that low enough spec for you. 
I used the xubuntu alternative disk.
its working fine

---

### Post by AhrenBa on 2006-07-16
Awesome, I just tried xubuntu and the boot errors occurred again. Does anyone know why this is happening?

I have successfully booted the Knoppix, MEPIS, DSL, and SLAX live cds, but for some reason ubuntu and xubuntu is having problems.

---

### Post by AhrenBa on 2006-07-17
Ok, I just checked the MD5sum of the download and they were the same, so that rules out a bad download.

Once again, other live cd's were working fine.

Also, when I tried the alternative xubuntu cd, it got a little further, but stopped and said "cannot mount cd". Why is this?

Ok, right when the cd starts up this is the first error I get:

*ACPI Unable to locate RSDP*

---

### Post by Choad on 2006-07-17
try the boot parameter  acpi=off

---

### Post by AhrenBa on 2006-07-17
> **Choad said:**
> try the boot parameter  acpi=off

Sorry, I am pretty new to Linux, but am pretty advanced with computers.

How and where do I get to the point where I can input this line you told me? Thanks

---

### Post by AhrenBa on 2006-07-17
Ok, when the ubuntu menu came up, I hit esc and went into text mode. I then typed in ACPI=off and got the error message, "Could not find kernel image".

---

### Post by AhrenBa on 2006-07-17
I hate to bump topics....but.....bump. :)

---

### Post by AhrenBa on 2006-07-17
Hmmmmm....If this is not going to install, I might as well find another good distro.

Can any of you recommend a good one besides ubuntu, kubuntu, and xubuntu?

---

### Post by AhrenBa on 2006-07-18
Ok, I just found out my cd rom is set as a secondary master. Does this tell me anything? Thanks

---

### Post by Choad on 2006-07-18
sorry i havent checked the forums for a while

iirc, you press something like f5 or f6 on the menu when it lets you choose to install, check cd for defects etc.

it has a thing at the bottom telling you what stuff does anyway.

basically you'll hit it and it will bring up a long line of text which you wont understand (these things are the default boot parameters)

each parameter is separated by whitespace (or "blackspace" in this case lol) 

just add at the end 

"acpi=off"

without the quotes and hit enter. the error message you recieved is because the first word has to be the kernel image to load. so for example to load the live image, you would type 

"live acpi=off"

or the server image

"server acpi=off"

other common fixes are "noacip" and "nolapic"

---

### Post by AhrenBa on 2006-07-18
Hello,
Thanks for the suggestions. I tried what you suggested and the error, "ACPI: Unable to locate RSDP" did not come up which is good. 

However, when it got to the point, "mounting root file system" it took like 5 minutes and went to the screen where "Buffer I/O error on device hdc, logical block 0" keeps displaying. It won't get past this point. Any ideas?

---

### Post by Choad on 2006-07-18
hmmm im out....

could try another forum like linuxquestions.org

the problem with ubuntu being so newbie friendly is that the forum is full of people who know little about linux :(

---

### Post by Charco on 2006-07-27
Oh wow, someone else in the world has the same wierd problem! I get that SAME error except its hdd, not hdc. 

Buffer I/O error on device hdd, logical block 1
Buffer I/O error on device hdd, logical block 2
Buffer I/O error on device hdd, logical block 3
Buffer I/O error on device hdd, logical block 4
Buffer I/O error on device hdd, logical block 5
Buffer I/O error on device hdd, logical block 6
Buffer I/O error on device hdd, logical block 7
Buffer I/O error on device hdd, logical block 0

I'm completely new to Linux too and I have no idea what this is or how to fix it, but it is really wasting a lot of my time because the boot takes forever! If you ever find the answer please do share. Thanks and good luck.

---

### Post by A2A on 2006-07-27
Just a few thoughts
Are there bad sectors on the Hard Drive?  
Is the drive attached to the primary IDE controller as Master?  Is is a SATA/SATA2 Drive? I know SATA installs in Windows need seperate drivers... Not sure about Ubuntu though.

Hope this might help in some way...

---

### Post by altonbr on 2006-07-29
> **AhrenBa said:**
> Ok, I just checked the MD5sum of the download and they were the same, so that rules out a bad download.

Once again, other live cd's were working fine.

Also, when I tried the alternative xubuntu cd, it got a little further, but stopped and said "cannot mount cd". Why is this?

Ok, right when the cd starts up this is the first error I get:

*ACPI Unable to locate RSDP*



I had the exact same problem, but mine went like this:

Uncompressing Linux... ok, booting the kernel
[4294667.296000] ACPI: Unable to locate RSDP

it then proceeded to boot up the LiveCD and session but struggled through the installer and froze between step 2 and step 5.

I tried the live CD on newer computers (but without installing) and that "[4294667.296000] ACPI: Unable to locate RSDP" error didn't come up.

The error came up on a old Pentium1 and Pentium2 but not newer 3's or 4's.... also, the Pentium2 machine BURNED (without actually being a CD burner) my Xubuntu LiveCD so now I'm on my 3rd copy... so I replaced the old drive with a newer DVD drive, to see if it was the computer and not the CD, but still no luck, that error comes up again.. and plus, like I said, it came up on my old Pentium1.

So I'm going to try the alternate CD.

---

### Post by kash on 2006-07-29
hello.
     I have a problem regarding installation and loading of ubuntu. Everything of the installation part goes on well, but when it starts to boot, it halts at a point where the display is "hotplug subsytem". at this point the booting process stops and never seem to continue. Can anyone help??.
     

   Anyways, regarding the I/O buffer problem... i thought this information might be useful.
 hda stands for - the primary master IDE hard disk
 hdb stands for - the primary slave IDE hard disk
 hdc stands for - the secondary master IDE hard disk
 hdd stands for - the secondary slave IDE hard disk.

---

