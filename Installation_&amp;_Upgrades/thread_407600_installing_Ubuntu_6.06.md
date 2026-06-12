---
title: "installing Ubuntu 6.06"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by Dave Otter on 2007-04-12
I am trying to install Ubuntu 6.06 onto my PC.Previously running Windows XP but got infected by Win 32 and now unablt to load.
    I have 2 HDD's 10 G and 38G.
 Have installed to smaller HD but cannot acsess the other one-on which Win XP was installed.
   Suggestions please but keep it simple as I am new to Computers
               
                    Thanks
#                              D Otter

---

### Post by KitChy on 2007-04-12
What was the filesystem of the hard drive that you cannot access? NTFS? If so go here:

[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)

---

### Post by Dave Otter on 2007-04-12
Sorry-How do I find out?

---

### Post by KitChy on 2007-04-12
Have you ubuntu installed or are you still running windows? If you're using windows, right click the hard drive and click properties and it will tell you in there. If you're using Ubuntu type into terminal (applications>accessories>terminal) and type "sudo fdisk -l" minus the quotation marks. It will ask you for the password you set up at installation to continue. This will then list all hard drives + partitions / sizes. From here you will be able to figure out what filesystem the hard drive is

---

### Post by Dave Otter on 2007-04-12
Have installed Ubuntu but having to use my sons PC using windows to get on internet. 
   Will have a go at what you suggest.
                             Many thanks
                                           Dave Otter
]

---

### Post by zvacet on 2007-04-12
Do you mean you can not choose wich OS to run(windows not showing in grub),or you can boot both of them but you don´t have access from Ubuntu to win?

---

