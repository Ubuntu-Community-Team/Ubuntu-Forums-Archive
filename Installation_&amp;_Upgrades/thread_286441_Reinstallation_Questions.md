---
title: "Reinstallation Questions"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by tetherblood on 2006-10-27
Hi guys,

im planning a full reinstall and reformat of my harddisks because my partitions and files are very untidy. Ive backed up all my data (films, music, images, doccuments, files etc) and some essential firmware and docs for my internet connex online and on CD's and have created and tested my Ubuntu 6.06 and Windows XP Pro CD's.

My question is about what is the best way to go around this? I have two hard disks the Primary is 80gig and currently has 4 partititions (Windows[20gig]/Ubuntu[10gigEXT3]/Ubuntu Swap[1gig]/Data[29gigNTFS]) and the 40gig is  soley for video [NTFS].
[LIST]
Should I install Windows or Ubuntu first after formatting the disks?
[/LIST]
[LIST]
What would people reccomend as ideal partition sizes for the system partions? (i primarily use Ubuntu and boot to windows for games)
[/LIST]
[LIST]
Should Windows and Ubuntu go on seperate hard disks?
[/LIST]
[LIST]
How do i create data drives/partitions (for music/images/video) that can be read/written to in both linux and windows?
[/LIST]

Thanks in advance

Matt

---

### Post by Craigus on 2006-10-27
You'll have to format the common-use partition as FAT32.

---

### Post by tetherblood on 2006-10-27
Cool thanks, thats one query answered.

I know its really my own discretion what the size of the partitions will be but would it be absurd to have a 10gig ubuntu ext3 partition for example.

The main answers i really want are will installing ubuntu first create problems when coming to install windows and will having ubuntu on the primary disk and windows on the secondary have any benefits?

Cheers,

---

### Post by Craigus on 2006-10-27
I don't know that 10 Gb is overkill necessarily - it depends what applications you are planning to install.

Unsure about benefits, but XP likes to believe it is on the primary drive. There is a workaround that can be done in grub to make XP boot from the secondary drive however. I can't post it just now as I'm using the Edgy LiveCD.

---

### Post by Coelocanth on 2006-10-27
You'd be best served to install XP first. If you don't, it will overwrite your GRUB, and you'll then be unable to boot Ubuntu without going through a bit of work. XP first, then Ubuntu, and you should be fine.

---

### Post by tetherblood on 2006-10-27
Thanks guys thats alot of help.
Wish me luck :cool:

---

