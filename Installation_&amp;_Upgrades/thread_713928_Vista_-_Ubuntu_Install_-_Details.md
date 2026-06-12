---
title: "Vista - Ubuntu Install - Details"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by miamizsun on 2008-03-03
Can't get windows vista to recognize or open the 7.10 iso that i burned to cd.

i have used vista to make a 50 gig partition(unformatted) for ubuntu and a 2 gig partition(fat 32) for a swap.

any advice would be appreciated as i am a noobie to linux.

current OS:

MS Vista Home Premium

2.80 GHz Intel Pentium D Processor 820

1024 MB DDR2 Memory

250 Gig HD

Intel Graphics Media Accelerator 950

Brand: E-machine

Model: T5224

---

### Post by taurus on 2008-03-03
What do you mean with the first statement?  Why would you want to open the ISO image?  You just burn it directly to a CD with a burning software so you can boot from it.  Unpacking and burning it to a CD will not work.

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29)

Have you rebooted your machine with the CD in the drive?  Make sure you have CDROM as a first bootable device in the BIOS.

---

### Post by miamizsun on 2008-03-03
thx for the speedy reply.

yes i have vista installed. i dwnlded the 7.10 iso and burned to a disc (i have done this twice), and i have rebooted but no dice.

for what it is worth i have a 6.06 CD that was mailed to me and it boots from the same drive without any snags. should i install the 6.06 instead? i tried and got to the 4 or 5 screen and i wasn't sure which drive went where. i want the dual boot option but vista to be the MBR.

am i making any sense? :)

regards

---

### Post by taurus on 2008-03-03
Does it boot from the CD, Gutsy, at all?  Have you tried booting that same Gutsy CD with another machine to make sure it's not the CD?

---

### Post by dstew on 2008-03-03
Did you burn the .iso as an image? If you just put the .iso on the CD like you would any file, it will not work. You need to burn it as an image.

---

### Post by miamizsun on 2008-03-03
ok, i dwnlded the ISO burner and reburned the 7.10 CD and it boots from it! thx!

i get to the step 4 of 7 and i'm not exactly sure what to do.

Here's what i see:

    /dev/sda

             /dev/sda1    ntfs     /media/sda1     10396 mb [COLOR="Red"](this is my MS Vista recovery)[/COLOR]

            /dev/sda2     ntfs    /media/sda2      184890 mb [COLOR="Red"](this is my MS Vista OS)[/COLOR]

            /dev/sda3                                      52568 mb unknown [COLOR="Red"](my partition for Ubuntu)[/COLOR]

            /dev/sda5     fat32                           2200 mb [COLOR="Red"](my partition for swap)[/COLOR]

since I don't know as much about Ubuntu, and because Vista doesn't like to take a backseat, I read that I should let Vista be the MBR. Once baptized, and as I learn, I plan to go into Linux in much more.

please advise.

regards, miamizsun

---

### Post by miamizsun on 2008-03-03
> **miamizsun said:**
> ok, i dwnlded the ISO burner and reburned the 7.10 CD and it boots from it! thx!

i get to the step 4 of 7 and i'm not exactly sure what to do.

Here's what i see:

    /dev/sda

             /dev/sda1    ntfs     /media/sda1     10396 mb [COLOR="Red"](this is my MS Vista recovery)[/COLOR]

            /dev/sda2     ntfs    /media/sda2      184890 mb [COLOR="Red"](this is my MS Vista OS)[/COLOR]

            /dev/sda3                                      52568 mb unknown [COLOR="Red"](my partition for Ubuntu)[/COLOR]

            /dev/sda5     fat32                           2200 mb [COLOR="Red"](my partition for swap)[/COLOR]

since I don't know as much about Ubuntu, and because Vista doesn't like to take a backseat, I read that I should let Vista be the MBR. Once baptized, and as I learn, I plan to go into Linux in much more.

please advise.

regards, miamizsun:grin:

*shameless bump*

---

### Post by dstew on 2008-03-03
Be brave. Go ahead and format that /dev/sda3 partition ext3, give it the mount point / , and make /dev/sda5 swap. Then, install grub into the MBR of (hd0). If you are not happy with the grub multiboot menu, or can't get Vista to boot, it is fairly easy to put the Vista bootloader back with the FixMbr command from the [ Windows Recovery Environment]("http://support.microsoft.com/kb/927392"). Unless you have some unusual logical volume management setup, track 0 of any hard disk is not part of any partition. It is reserved for the MBR and any extra boot program that might fit (like grub stage1.5). Unless you deliberately put grub into the partition, it won't bother Vista.

---

### Post by miamizsun on 2008-03-03
thx D, i'll give this a try tonight. regards, miamizsun

---

### Post by miamizsun on 2008-03-04
[SIZE="7"]**[COLOR="DarkOrange"]L Yeah!!![/COLOR]**[/SIZE]

**thx guys - working like a charm - so far so good!**

---

