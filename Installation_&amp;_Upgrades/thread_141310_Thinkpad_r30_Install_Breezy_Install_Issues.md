---
title: "Thinkpad r30 Install Breezy Install Issues"
date: 2006-03-08
forum: Installation &amp; Upgrades
---

### Post by zerocool1014a on 2006-03-08
i just recieved my mail copies of breezy and went to install i boot and it freezes when detecting cd rom 87% i looked and found the solution for that which was to boot using

linux irqpoll noapic nolapic

however it does get past that area now and lets me partition then starts copying files after some time however it locks again im not sure why but i just cant seem to win i have had xanderos and windows installed on the machine with no problem i will post with more detail of where it is freezing but does anyone have ideas why i might be having soo many issues?

---

### Post by zerocool1014a on 2006-03-08
okay i have the install running and it goes past everything fine untill it reaches

Installing the base system

6%

retrieving libpam0g...

then it freezes.. i will try again to see if it gets past this point but it has done about the same thing with two different burnt disks from two different images that both checked out with md5 and the disk im using now was shipped to me so i dont think its a disk problem i will keep trying though any ideas are welcome.  Thanks

---

### Post by zerocool1014a on 2006-03-08
okay further update

it is still freezing at 6% during installing the base system but the file it was retrieving is different  anyone have any ideas of what might cause this there is no noise from my cd rom drive, no noise from my hard drive and no network activity from my network adapter also the fan on my processor isnt running nor does it feel warm at all any ideas at all would be greatly apriciated..

---

### Post by zerocool1014a on 2006-03-08
alright another update i think i may have it finally :)

linux acpi=off no acpi

no problems so far i have my fingers crossed i will post back if this works

---

### Post by zerocool1014a on 2006-03-08
okay im a total noob that worked i should have searched harder in the first place sorry for poluting the forum hopefully my next post will be from inside ubuntu on my laptop

---

### Post by crendon on 2006-04-15
Ok Ill continue this threat hopping somebody appear and help me. It seems the owner of this theat is not around here anymore so I take it as mine now hohoho!
Anyway summarizing:
To success intalling Ubuntu Breezy on a Thinkpad R30 the command is:

#linux floppy=thinkpad acpi=off noacpi

Soon after finish the installation ubuntu update manager will ask you to get some bug fixes and new program version... but after update the system and reboot the machine your sound card won't work... reason unknow... i found by google this solution; open the terminal and load this file:

#sudo nano /boot/grub/manu.lst

Find the line that starts with "#kopt" or "Kopts" and add at the end these options:

 acpi_irq_isa=10 apm=off

Save the file and reboot the grub file with:

#update-grub

Finally reboot the machine and your sound card will be working again.
Then this is the next challenge... I have some problems with PCMCIA cards. I use a MELCO wireless PC-Card and a Buffalo USB-x2(2.0) extention card. I have just one PC-Card slot so i have to alternate them sometimes. When I stop my wireless eth1 and unplug it something strange happen... ubuntu start not work properly and kinda freeze for a moments... if i want to plug my other pc-card ubuntu doesnt recognize it (It does when it is plugged in a free boot up). If i turn off my laptop it freeze in the middle of the proccess. I think this erratic behave is because the new kernel that ubuntu make us load soon after install the system.
Any ideas?

PS: I am not native english speaker... please forgive my grammar and spelling mistakes.

---

### Post by crendon on 2006-04-21
ok I figure it out. To install breezy without sound and CD unit access problems we need to use the following command:

#linux floppy=thinkpad acpi=off noapic apm=off acpi_irq_isa=10

I used this command in a fresh install and now the R30 works without problems. Now I am working on "hotswap"... it is usefull to change the ultrabay CD unit with the Ultrabay floppy disk (swap)... it stop the device correctly but when we need want to load the ultrabay floppy or CD unit again it doesnt recognize it.
If i get any progress ill let you know.
PD: I still have problems loading my USB (SCSI) hard disk. It makes my system ger freeze. I have this problem just with the USB HD... no problems with USB pens or digital cameras.

---

### Post by EdgardPacheco on 2006-06-30
Thanks, I used the code 

#linux floppy=thinkpad acpi=off noapic apm=off acpi_irq_isa=10

and then everything went well, till it entered to make the partitions, and the screen went black and it appeared:

killed
killed
killed
killed
............

and it never stops saying "killed", anyone knows what problem do i have??

---

### Post by jbennet on 2006-07-24
I had the same problem on mandriva one and i did:

live noapic nolapic acpi=off acpi=no

and it ran fine (but had soooooooo many warnings)

---

### Post by crendon on 2006-09-29
This also works and seems less troublesome

floppy=thinkpad pci=noacpi

I hope it is helpfull for you guys

---

