---
title: "ntfs partiotions not accesible"
date: 2005-08-03
forum: Installation &amp; Upgrades
---

### Post by AlexDM on 2005-08-03
Hi , 

this is my fisrt installation of Ubuntu and only the second try with Linux ( first one was Mandrake some time ago )

    Firstly I am sorry if I posted in the wrong section or if the problem has been already solved... 

My bigest problem right now is  that I can not acces my NTFS partitions .

- /mnt/ is empty ( I remeber that in Mandrake that was the plays for the Windows partitions )
- If I go to System -> Storage Media  the location "media:/" opens and I see all my logical drives BUT only the partition with Ubuntu has a litle green sign and is accesible. All the others are just shown but when I double click on them it says :

 " the device can not be mounted 
   can't find dev/hda5  in etc/fstab or etc/mtab "

  - I am a newbe to linux and to ubuntu even more so any detailed help would be greatly apreciated.

---

### Post by tkteo on 2005-08-03
[QUOTE=AlexDM]Hi , 

this is my fisrt installation of Ubuntu and only the second try with Linux ( first one was Mandrake some time ago )

    Firstly I am sorry if I posted in the wrong section or if the problem has been already solved... 

My bigest problem right now is  that I can not acces my NTFS partitions .

- /mnt/ is empty ( I remeber that in Mandrake that was the plays for the Windows partitions )
- If I go to System -> Storage Media  the location "media:/" opens and I see all my logical drives BUT only the partition with Ubuntu has a litle green sign and is accesible. All the others are just shown but when I double click on them it says :

 " the device can not be mounted 
   can't find dev/hda5  in etc/fstab or etc/mtab "

  - I am a newbe to linux and to ubuntu even more so any detailed help would be greatly apreciated.[/QUOTE]
 Hi. I had the same problem as you. I could not access my NTFS partitions on two different hard disks after initially installing Kubuntu. I searched the keyword "mount" on these forums, and found some answers. Can't help you much cos I am probably even more newbie than you are, but in one of the threads I found in search, there's a link to some Ubuntu wiki page that describes how to find out and type in the information about your NTFS partititions into the /etc/fstab text file.

After following the instructions I am able to successfully access all the partitions on my hard disks. Edit: the link is at:

[https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions)

---

### Post by AlexDM on 2005-08-03
[QUOTE=tkteo]Hi. I had the same problem as you. I could not access my NTFS partitions on two different hard disks after initially installing Kubuntu. I searched the keyword "mount" on these forums, and found some answers. Can't help you much cos I am probably even more newbie than you are, but in one of the threads I found in search, there's a link to some Ubuntu wiki page that describes how to find out and type in the information about your NTFS partititions into the /etc/fstab text file.

After following the instructions I am able to successfully access all the partitions on my hard disks. Edit: the link is at:

[https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions)[/QUOTE]
 thank you . I'll try the advice from the link as soon as I get home.

---

### Post by avantgardaclue on 2005-08-03
[QUOTE=AlexDM]thank you . I'll try the advice from the link as soon as I get home.[/QUOTE]
 These instructions worked perfectly for me too... thankyou

---

### Post by Drain on 2005-08-03
Another excellent guide (that is a lot shorter on explaining how/why things work and getting straight to work) is [www.ubuntuguide.org](www.ubuntuguide.org) ... and in fact, they answer your question right here:

[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by AlexDM on 2005-08-03
[QUOTE=Drain]Another excellent guide (that is a lot shorter on explaining how/why things work and getting straight to work) is [www.ubuntuguide.org](www.ubuntuguide.org) ... and in fact, they answer your question right here:

[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)[/QUOTE]
 Thanks  guys.... you were very promt and exact. It worked for me too. I'll go and read now the starter guide... in minimize other "newbe" questions. Thanks for not bashing me for the first question :)

---

