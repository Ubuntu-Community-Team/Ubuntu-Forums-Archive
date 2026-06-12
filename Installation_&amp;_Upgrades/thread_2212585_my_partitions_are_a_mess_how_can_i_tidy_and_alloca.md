---
title: "my partitions are a mess how can i tidy and allocate?"
date: 2014-03-21
forum: Installation &amp; Upgrades
---

### Post by isla on 2014-03-21
Hi, first of all i'm sorry if I do not ask in the right way - i'm a total newbie.

I can however see my partitions are totally messy. i've got 2x unallocated spaces, i've got gda 5 and 3 but can't see 2 or 4, (trying to go by memory here) and I think ubuntu is on the gda5 but, i really can't be sure...but i want to allocate the majority of space to ubuntu now that i've got it up and running well.

i've looked at the official ubuntu documents showing how to do this, and many websites but i can't relate to it - mine looks so different. I don't get little pictures of keys and I don't know which ones are out of use. I can't risk losing my ubuntu settings and everything it's taken so long to get wine and pipelight and netflix and lots of little things to work considering i don't know what i'm doing! 

please can anyone go through the terminal commands and results and help me work out which partition to extend - and how to get rid of or allocate the rest?

i do have a little gda1 or something for the windows reset thing so i know to leave that alone.

thankyou and very very sorry for messy questions and lack of knowledge

isla :D

---

### Post by isla on 2014-03-21
this may be another topic but i have also been advised to flash  the BIOS or something because i cannot get my fan to work correctly - however i have posted about this problem also but no help as yet. just mentioning it incase this is something i should do at the same time... sorry.

---

### Post by Hodevah on 2014-03-21
Hi. Firstly, you do NOT need to flash your BIOS just because your fan isn't working. That's an internal hardware thing. You would need to bring it to a computer tech and he will either install a new one or fix your current one. Fans and BIOS are not entirely related.   Also, fans are fairly cheap these days.    Who advised you that you need to flash your BIOS? What is the web-link for this please? You need to understand that suggestions for BIOS flashing are virulent around the net. Take flashing with a grain of salt. In many cases you don't need to flash. Flashing is more common for gaming.    Secondly, with respect to your HDD partition concern, Open Terminal and    ```
lsblk 
```   to check which drives your linux-box can see,    ```
sudo fdisk -l
```

---

### Post by isla on 2014-03-22
ok i'll go back to the partition thing cos i think i can actually do that...may i ask for help on understanding the results and then what it is i can either shrink or get rid of in order to extend the right partition?
here are the results anyway...
ila@computeris:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0  74.5G  0 disk 
&#9500;&#9472;sda1   8:1    0  11.7G  0 part 
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9500;&#9472;sda3   8:3    0  23.3G  0 part /
&#9492;&#9472;sda5   8:5    0  31.5G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom

---------------------

what linux can see

Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    24563384    12281661   12  Compaq diagnostics
/dev/sda2        24563446    90638729    33037642    f  W95 Ext'd (LBA)
/dev/sda3   *    90652672   139480796    24414062+  83  Linux
/dev/sda5        24563448    90638729    33037641   82  Linux swap / Solaris


you see i don't understand what i'm looking at..i don't know what a swap file is - ...i would just like to devote as much 
space to my unbuntu as poss. i don't use the comp for much just watching films and surfing the net but it tells me
i only have 17gb allocated and it used them all up or something. i'm terribly sorry about being so useless. and thankyou for
your help.  I have put a post up for help with the fan and not getting help with it yet but will keep asking as it is
an ubuntu meets acer laptop issue...the fan works - for windows, it also works if i turn on the computer quickly after it cuts
out from heat so the fan detects it on starting up and stays on forever until i have to restart ubuntu because my netflix
goes jumpy so...its a boring list of events! i have installed scripts to start on start up that others have used for this
exact same problem and some have managed to get it to work. but i think because i don't know how to correct the right 
commands in the script it probably isn't working because of that..or something else. tried a few things but yeah no joy,
i'll keep updating that post until someone tells me it can't be helped or is willing to go through the script and 
instructions with me. 

thankyou so much for helping
isla 
(if u are wanting to to look this is that post but really i am just happy that you might be able to help me with altering 
the partitions :-D [http://ubuntuforums.org/showthread.php?t=2208306&highlight=isla](http://ubuntuforums.org/showthread.php?t=2208306&highlight=isla) )

---

### Post by nibal on 2014-03-22
> **isla said:**
> ok i'll go back to the partition thing cos i think i can actually do that...may i ask for help on understanding the results and then what it is i can either shrink or get rid of in order to extend the right partition?
here are the results anyway...
ila@computeris:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0  74.5G  0 disk 
&#9500;&#9472;sda1   8:1    0  11.7G  0 part 
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9500;&#9472;sda3   8:3    0  23.3G  0 part /
&#9492;&#9472;sda5   8:5    0  31.5G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom

---------------------

what linux can see

Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    24563384    12281661   12  Compaq diagnostics
/dev/sda2        24563446    90638729    33037642    f  W95 Ext'd (LBA)
/dev/sda3   *    90652672   139480796    24414062+  83  Linux
/dev/sda5        24563448    90638729    33037641   82  Linux swap / Solaris


Swap file is your virtual memory - real memory. I.e. memory on your disk. When your real memory runs out, your PC uses your disk. Slower, but cheaper.
As a rule of thump, it should be the same size as your real memory, unless you have special needs.

sda1: Compaq Diagnostics. i don't know if you really need them. If you don't you can delete them with fdisk.
sda2: Windows partition. You have, or install windows there.
sda3: Your Ubuntu. It is also your bootable partition (*).
sda5: Your swap.

You can delete, move, create and join partitions with fdisk. But you need to be expert to do it.
It would be easier for you to reinstall Ubuntu and repartition it during the installation.

 HTH

---

### Post by grahammechanical on 2014-03-22
May I add something? I may confuse you more but stay with us and it will become less confusing. Your partitions are not in a mess. Please accept that. Now about partitions.

If we have a motherboard that has a BIOS then we can only have 4 Primary partitions on the hard disk. There is a way around this. We can make one of the Primary partitions into a special primary partition called an Extended partition and then in that Extended partition we can create any number of other partitions that are called Logical partitions.

It is usual practice for the Ubuntu installer to put Ubuntu into a Primary partition if less than 3 Primary partitions already exist. Then the installer uses another Primary partition to create an Extended partition and in that partition the installer then creates a Logical partition to be used for Swap.

So, on your hard drive sda1 is a Primary partition and so is sda2 and sda3. Then sda4 which you cannot see is primary partition number 4 and you cannot see it because it is an Extended partition. That means that the swap partition has to have the next number and that is sda5 and sda5 exists inside sda4.

When I first installed Ubuntu back in 2007 I used an empty hard disk and Ubuntu was on sda1 and the swap was on sda3. So, where was sda2? That was the Extended partition that was holding sda3. This is how things are done. This is why I say your partitions are not a mess.

The Windows OS uses a swap file but Linux uses a swap partition. When our system memory (RAM) gets used up the OS will stop working unless it makes space in memory for more data and it does this by paging data out of RAM onto the hard disk either into a swap file (as in Windows) or into a swap partition (as in Linux).

It is not unusual to have small amounts of unallocated space. I have some on my two hard disks and I have many partitions because I have few installations of different version of Ubuntu. Space is allocated to partitions in small chunks and it seems that the partitioner is putting the partitions as close as it can get but the partitions do not always meet fully side by side.

By the way if the hard disk already has 3 Primary partitions then the Installer will create a 4th primary partition and make it an Extended partition and in the Extended partition it will create two logical partitions, one for Ubuntu and one for swap.

Regards.

Here is a question for you. Why is your swap partition 31.5 GB when 3 GB might be a bit on the excessive side?

---

### Post by isla on 2014-03-22
Thanks for all your advice so far people! i'm well chuffed :-)

i simply did not know what i was doing when i installed ubuntu - i was just winning it. i had windows xp pro before and microsoft stopped supporting it and that was it I had nothing else to go on. I don't have money to by a new operating system.
So..the swap file came when i was just clicking about trying to make the goddamn thing work...i figured if i just clicked around for long enough something would happen. thats generally how i get on with comps and it does get me somewhere usually.

[**[COLOR=#000000]nibal[/COLOR]**]("http://ubuntuforums.org/member.php?u=1798490") thankyou for listing it in a way i can understand :-)
That is why i can't re install ubuntyu - it has been too much hard work trying to get netflix to work, i do not know how i managed it but i had to install loads of things - wine pipelight and other weird names then i had to fiddle with the settings in the scripts until it worked, i would rather work out what is the best thing to do with the partitions i have created.

[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323") thankyou for explaining - i understand it a little bit more now :-) I would like to reduce the swap and give that space to my ubuntu partition...i don't actually know how to do that - the terminology when i'm in that partition manager is all gobbledeegook. do i shrink the swap and then...how to i grab that space and say i want to allocate it to the main partition for ubuntu? if this is too much to ask - i would also appreciate being pointed towards the right instuctions - i can read and learn if i go over it enough times but i'm just not sure what the question is if you know what i mean...:-)

---

### Post by fantab on 2014-03-23
The most commonly used disk management utility in Linux is Gparted: [Tutorial]("http://www.dedoimedo.com/computers/gparted.html").

---

### Post by Hodevah on 2014-03-23
> **fantab said:**
> The most commonly used disk management utility in Linux is Gparted: [Tutorial]("http://www.dedoimedo.com/computers/gparted.html").  I agree. If, and only if you really wanted to go ahead and redo all your partitions (even though it's not necessary) you could via gparted or by using the ubuntu-remix cd,  repartition your entire HD. That of course would (1) take time and (2) you would lose all your partitions in favor of how you want your partitions to look like and what you want to have installed on them. It's easy enough to do if you know how. You have many options.  Also, as a rule of thumb, if you do place any output from terminal here in your posts, don't forget to use the code tags

---

### Post by nibal on 2014-03-23
> **isla said:**
> Thanks for all your advice so far people! i'm well chuffed :-)

i simply did not know what i was doing when i installed ubuntu - i was just winning it. i had windows xp pro before and microsoft stopped supporting it and that was it I had nothing else to go on. I don't have money to by a new operating system.
So..the swap file came when i was just clicking about trying to make the goddamn thing work...i figured if i just clicked around for long enough something would happen. thats generally how i get on with comps and it does get me somewhere usually.


I suggest you to reinstall Ubuntu. It takes ~ 2hrs unattended, and you can repartition it the way you want it. You will loose data if you repartition during installation, so you should backup anything you have useful - not the ditsribution, this will be installed from the CD. Just before installing the files, ubuntu will ask you where you want to install it. The last option, I believe, is to repartition the disk yourself. That's the one you want. As Grahammechanic said, your partition layout is not bad. But it could be better:

1) Compaq partition, if you don't need it for linux, delete.
2) Windows partition. If you don't need it no more, you can delete that too. It is good, though, to keep another OS around, even if it is no longer supported.
3) That's where i usually create my swap. In the middle of the disk for quick access. Give it the same size as your RAM.
4) Give everything else to Ubuntu.

With only 3-4 partitions you can have them all primary. This should be slightly faster access, too. If you repartition yourself, the installer will prompt you with partition type. Just put primary there.

GL,
Nikos

---

### Post by isla on 2014-03-23
hmm ok that's really clear thankyou - i seem to remember clicking around that partition manager was quite complicated for me but i will just read up on that bit again there are plenty posts in the forum of pics of that bit.

better double check what i am doing....do you think i could practise with the live media thing (you know when you run the cd and you can access the partition manager that way i nearly did it the other day but got scared and cancelled the pending changes and backed out)

maybe i could have a go on that and then come back here if i have more questions about how  to get on with this.

One more question - i have backed up twice onto the ubuntu Backup. does that back up the scripts i had to alter for pipelight and things like that. it says it is backing up my home folders but new to ubuntu i am not sure what home folders covers entirely.  

thanks so much for your advice again 
isla

---

