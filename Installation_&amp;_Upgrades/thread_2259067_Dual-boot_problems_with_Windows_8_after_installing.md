---
title: "Dual-boot problems with Windows 8 after installing Ubuntu 14.04"
date: 2015-01-01
forum: Installation &amp; Upgrades
---

### Post by marcel12 on 2015-01-01
Dear friends,

I am a beginner with Linux and I had a bad inspiration to try a quick Ubuntu installation without reading properly about it first.

I found a tutorial and have installed Ubuntu on my laptop (Gateway NV56R30u) alongside pre-installed Windows 8. I have made a recovery disk first of my Windows 8 and saved it on a 8Gb USB pen drive (it used 2,6 Gb of it).

The installation of Ubuntu went flawlessly. After re-boot it started with that screen with Ubuntu logo on it, but no GRUB screen as expected, where there should have been the option to choose between Windows and Ubuntu. I tried to find a solution for my problem and found that I need a Boot Repair...I used boot repair several attempts but it partially solved my problem...I now starts with a GRUB welcome screen, but there is still no option to choose Windows...

Here you can also see my BoorRepair report: [http://paste.ubuntu.com/9654931/](http://paste.ubuntu.com/9654931/)

Having analysing what I've done wrong I found that I've done a huge mistake with partitioning.... I have a 1TB HDD, which I have split as follows: 50 GB for Ubuntu and the remaining amount of space I have split in half: one half for Home and another half for Swap drive...I believe I am the only idiot on this planet who have ever done this...:-) This is how my partitions look now: [http://imgur.com/a/CBfXu#0](http://imgur.com/a/CBfXu#0)

The idea was to have both systems installed together in order to have the possibility to learn Ubuntu while having Windows for my windows-based programs...

Now I don't know what to do, as I have a few questions I don't have an answer...

Let's say I could use the recovery drive to backup Windows, but I've got these questions, which may look stupid and I would appreciate some good answers:

1. How bad can affect my data from HDD my "genious" way to do the partitioning? Is it reversible?
2. Considering the way I have done the partitioning, if I decide to use recovery drive to repair Windows, what are my chances to have a good result,without loosing all my data? But honestly...I thing it's an illusion...:-)

Trying to answer myself to those questions I have searched lots of forums, including here and I realized that the app TestDisk may help me to figure out if I have messed up my hard disk. After using TestDisk I've got some results (you can see them in the above album), but I don't really know how to interpret them...

So, I would appreciate some advice in solving this mess I've done...

Ideally I would have these priorities to solve this problem:

Plan A: It would be great to make the dual-boot to work, so I could use both systems...
Plan B: In case plan A fails, I then prefer to come back to Windows and to be able to recover at least drive D (with the most important data) and C, if possible..

Plan C: To recover the major part of my data and to start a new life...:-)

I hope you will not tell me to ask google, as I have already did that and no other problem was as spooky as mine...

---

### Post by gordintoronto on 2015-01-02
First suggestion: stop using the computer! The more you use it, the less likely that you can recover data.

In fact, you did not install Ubuntu alongside Windows. You wiped out Windows and all your data. If you have your data backed up properly, this should not be a problem. Otherwise you will need to learn how to use Testdisk, and copy whatever it can recover to external media. Use another computer to read about Testdisk and another similar program, I think it's called photorec. 

Slow down, be organized.

---

### Post by oldfred on 2015-01-03
Since Ubuntu writes through the ext4 partition, there is really no chance to recover a fully working system. You may be able to recover some data as Linux is small and Windows has most of its data at beginning of drive.

Since you erased entire drive, there is no recovery partition either. Unless you made the set of DVDs to recovery system when hard drive fails, you have no way to recover.

Some vendors will ship you the recovery set of DVDs for your system for just a nominal charge, others do not and you have to purchase a entire new copy of Windows. The product key is now embedded in the UEFI and only works with the OEM or vendor version of Windows.
One user posted that he purchased from a local store and they still had same model for sale. They then made the recovery set from that computer.

---

### Post by marcel12 on 2015-01-04
Dear [**[COLOR=#000000]gordintoronto[/COLOR]**]("http://ubuntuforums.org/member.php?u=507940") 	 , thak you for your advice....Unfortunately I have used it since installing Ubuntu (30.12.2014)....and we were in holodays these days. I will contact one of or local recovery data service  to see there is something to be done...

---

### Post by marcel12 on 2015-01-04
Dear [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711"), thank you for your feedback!

I am sorry I have been disturbing you for my stupid mistakes! I hope to recover some important data and I will try another Ubuntu install next time...:-)

---

### Post by oldfred on 2015-01-04
Another user who reinstalled Windows & Ubuntu after erasing the entire drive.

 Erased entire drive, reinstalled Windows & Ubuntu
[http://ubuntuforums.org/showthread.php?t=2257711](http://ubuntuforums.org/showthread.php?t=2257711)

---

