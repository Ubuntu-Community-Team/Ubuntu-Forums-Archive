---
title: "[SOLVED] Upgrading to 8.04 from 7.04"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by venkat.raman on 2008-10-13
hi all

i am quite new to ubuntu, currently i am using 7.04 dual booting with XP. 

just got my hands on an 8.04 install disk.

sorry if below questions sounds stupid

i am wondering if it would be possible to upgrade from 7.04 directly to 8.04 (similar to windows) or i have to completely remove 7.04 and install 8.04 fresh. triple booting xp/7.04/8.04 doesnt look quite ok to me

in case i have to install 8.04 fresh, could you please suggest a way of going about it as i am extremely leery of losing my current set up which works just well? i have not seen any thing in the web giving instructions upgrading from 7.04-8.04. 

thanks

---

### Post by mpierce on 2008-10-13
No you don't read the FAQ as it tells you how. I use kubuntu so don't know how on ubuntu. I did it.

---

### Post by venkat.raman on 2008-10-13
sorry, but i am not able to understand your message.

anyway are you talking about the FAQ in the upgrade page ([www.ubuntu.com/getubuntu/upgrade)?](www.ubuntu.com/getubuntu/upgrade)?) i have seen there, it only shows how to upgrade from 7.10 to 8.04 among others.

could you also tell me how you did in kubuntu? i suppose the same would hold good for ubuntu too.

thanks

---

### Post by Partyboi2 on 2008-10-13
You would need to upgrade feisty(7.04) to gusty(7.10)  then to hardy(8.04.1), you would not be able to skip 7.10.  Always a good practice to backup before upgrading just incase.
Make sure that your feisty installation has all the current updates before upgrading and that you disable all 3rd party repos in Software Sources (System>Admin>Software Sources)

[http://www.howtogeek.com/howto/linux/upgrade-ubuntu-from-feisty-to-gutsy/](http://www.howtogeek.com/howto/linux/upgrade-ubuntu-from-feisty-to-gutsy/)
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by venkat.raman on 2008-10-13
ah yes, upgrading to 7.10 and then to 8.04;

using the upgrade manager gave me a dialog that i need to download 950mb of data!!!

is it ok to wipe out 7.04 entirely and install 8.04? i definitely cannot download close to 1gb of data just for an intermediate upgrade. 

if you do suggest 7.04 to be completely removed, can you also please suggest any website which gives me the info?

thanks for your help

---

### Post by Elfy on 2008-10-13
You don't need to remove anything to install - it will go over the top of the 7.04.

If you don't have seperate /home aprtition then that will be overwritten as well so backup - obviously docs etc but also e-mail settings are stored n your /home.

When you get to the partition part choose manual and you can install onto the current partition.

---

### Post by venkat.raman on 2008-10-13
ah..the reply i was looking forward to.

shall try loading 8.04 directly on 7.04 later in the evening (keeping all my fingers firmly crossed).

will i have to change the mbr to reflect the new version or will this also get taken care during the installation? 

i hope this wont lead to a triple boot or worse screw my system up fully...:-)

---

### Post by Sef on 2008-10-13
Read this [sticky]("http://ubuntuforums.org/showthread.php?t=849915").

>  shall try loading 8.04 directly on 7.04 later in the evening (keeping all my fingers firmly crossed).

Have an 8.04 cd handy as installing like that will cause your system to fail.

---

### Post by venkat.raman on 2008-10-13
shall go thru the page you have given.

of course i do have 8.04 cd. am going to install it from the cd..

thanks

---

### Post by venkat.raman on 2008-10-13
done upgrading with mixed results.

using the installer cd to install 8.04 over 7.04.. install went ok.

after install however, i have lost connection to the printer and to the central server.

but that again is another problem, another day.

now to close this thread after thanking everyone for their help.

---

