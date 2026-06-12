---
title: "Please Help want to remove ubuntu and grub"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by balkrish999 on 2010-03-07
hello i want to remove ubuntu .10 from my system i currenty have windows 7 and ubuntu 9.10 on a dual boot and the grub  . the reason for this is im going to install ubunut on another laptop and i want this laptop to just have 7. :P:P

i dont have any os disks as   my laptop did not come with any also ( its got a recovery partions )  

how do i get rid of uubuntu and grub and safly have windows 7 only like normally thanks what do i do how do i do it ? thanks

---

### Post by 2hot6ft2 on 2010-03-07
I'm sure it's pretty much the same as xp so here's what I saved on switching back to windows xp.
> **Monotoko said:**
> Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

That will fix XP right up :)
That would just leave deleting the ubuntu partition and expanding the win7 partition to take that space back.

And here's where you can download a windows 7 recovery cd.
[Download Windows 7 System Recovery Discs]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Might want to wait for others to respond in case something's changed, meanwhile you can start the disc download.

---

### Post by dgoodin on 2010-03-07
Would a similar procedure work for deleting a Windows partition?  I have a Sony laptoo that originally came with Vista.  I partitioned the disk and added Ubuntu.  I now have a virtual box running under Ubuntu.  I don't need three OS, so I want to eliminate the Windows partition.  How would I do this?

---

### Post by balkrish999 on 2010-03-07
can some1 please help

---

### Post by 2hot6ft2 on 2010-03-07
> **dgoodin said:**
> Would a similar procedure work for deleting a Windows partition?  I have a Sony laptoo that originally came with Vista.  I partitioned the disk and added Ubuntu.  I now have a virtual box running under Ubuntu.  I don't need three OS, so I want to eliminate the Windows partition.  How would I do this?
That's the opposite of what this thread is about so you would start by starting a tread for it otherwise you would be hijacking this thread. Taking a screenshot of GParted
System > Administration > GParted
and attaching it to your post **in the new thread** along with the results of
```
fdisk -l
```
in a terminal
Applications > Accessories  Terminal
would help to get answers when you start the tread since we don't know how your partitions are set up.

I'm sure more will chime in on this balkrish999 it may take a little while since it's Sunday morning but have faith.

---

### Post by balkrish999 on 2010-03-07
can some1 help me not someone else i made this thread and i need help plese!!!!!!!!!!!!!!!    help me

---

### Post by balkrish999 on 2010-03-08
hello i want to remove ubuntu .10 from my system i currenty have windows  7 and ubuntu 9.10 on a dual boot and the grub  . the reason for this is  im going to install ubunut on another laptop and i want this laptop to  just have 7. :razz::razz:

i dont have any os disks as   my laptop did not come with any also ( its  got a recovery partions )  

how do i get rid of uubuntu and grub and safly have windows 7 only like  normally thanks what do i do how do i do it ? thanks

---

### Post by oldfred on 2010-03-08
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.

I would not increase the size of the win7 partition but reformat the linux partitions to NTFS and use them for data. Do not use gparted to move the win7 partition, but you can use it to reformat the linux partitions. Download a gparted liveCD.

---

### Post by balkrish999 on 2010-03-17
can some1 please help i got windws 7 need step by step instucstion on what to do its on a dual boot wid windows 7 and ubunut

---

### Post by Mark Phelps on 2010-03-18
> **balkrish999 said:**
> can some1 please help i got windws 7 need step by step instucstion on what to do its on a dual boot wid windows 7 and ubunut

Oldfred propvided you some things to try.

If you're not willing to follow suggestions, then quit posting the same question over and over.

---

### Post by presence1960 on 2010-03-18
> **Mark Phelps said:**
> Oldfred propvided you some things to try.

If you're not willing to follow suggestions, then quit posting the same question over and over.

Before you remove Ubuntu, boot into ubuntu and open a terminal and run ```
sudo apt-get install lilo
```Ignore the warning.

next in terminal run ```
sudo lilo -M /dev/sda mbr
```Your MBR will now be fixed so that you boot right to windows. You can either remove Ubuntu's partition(s) from gparted with the Ubuntu Live CD or gparted Live CD.  You can also boot to windows and use it's disk management utility to remove the ubuntu partition(s).

Either way that you remove the ubuntu partitions you can then use windows disk management utility to merge the unallocated space with your C: drive or create another NTFS partition(s).

**_OP you now have a couple different ways to accomplish what you want to do. So now use the information please._**

---

