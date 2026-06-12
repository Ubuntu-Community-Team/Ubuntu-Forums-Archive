---
title: "Major problem-crash"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by hatmancan on 2008-11-12
Ok heres the problem..i downloaded kubuntu 8.10..let install over night and now i cannot get in to my comp..
i have made it as far as a root-boot..
there were 4 screens to choose from and neither will work..i tried recovery mode and here is a list of problems..

E:dpkg was interrupted,you must manually run 'dpkg --configure -a'to correct the problem..
did that and got too many errors.stopping

dpkgi ../../src/packages.C:265:process_queue!assertion'!queue.length'failed.
aborted

i need to get retrieve my files for work..
help asap
ty
hat

---

### Post by Steve1961 on 2008-11-12
use the live cd to access your files and copy them to a usb stick or other media

---

### Post by hatmancan on 2008-11-12
well steve how do you do that????
i have no idea on this..
i had to switch over to my xp hdrive ..
can i transfer files using live cd to my main hard drive?\
if so can you give me some instructions?
ty
hat

---

### Post by Steve1961 on 2008-11-12
If you boot from a live cd and then open the home folder (I think there's a folder called examples on the live cd, which is fine) you'll see a list of drives in the left hand side bar.  Just click on the drive you need to access and navigate to where your files are.  You should be able to copy and paste the files to another hard drive, or to a usb key.

Edit: I've just realised that you probably have a Kubuntu cd and not an Ubuntu one.  Shouldn't matter, but you might need to access the drives through my computer or something similar.  I don't use KDE so can't be more specific, sorry.

---

### Post by hatmancan on 2008-11-12
i have a cd which i got from ubuntu..
what is a live cd?
i am not used to all this new terminology?
i am on xp right now so i am marking and printing all info before i switch again..
do you have any step by step?
also i once got to a ubuntu main screen but mouse and keyboard will not work so it was useless to wait
hat

---

### Post by Steve1961 on 2008-11-12
A live cd is just a cd that you can boot from and which launches an operating system running from the cd - so it doesn't touch your hard disks.  The standard Ubuntu desktop cd is a live cd.  You boot from the cd into an Ubuntu environment, and then double click the 'install' icon on the desktop to install to hard disk.

I'm presuming you did this when you installed.  If not, what did you do?

---

### Post by hatmancan on 2008-11-12
yes i installed from the cd..
i have 2 hard drives
1 is windows and 2 is ubuntu...
i partitioned with somefile that was recommended.
i had kde , gnome kde4 desktop invironments ..
when i tried to install last one was when all the problems started..
also when i used to do a normal boot it would give me 2 recovery options along with 2 normal generic boots.. is this normal?
what happened is a used the instructions on the kubuntu site for downloading and used their recommendations for updates...
took overnight to install and i am on high speed here..
it came up to kde 3.5 desktop with 3 choices to login to..but could not use key board?
i think i may be better off to wipe and start all over once i get my files back
hat

---

### Post by Steve1961 on 2008-11-12
Right, that sounds complicated. If you have a fast connection I'd suggest grabing a standard ubuntu cd from ubuntu.com:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

you just need the standard desktop edition.  Once you have it you can use it to grab your files and then to reinstall a vanilla version of Ubuntu.  There's no point in creating too many complications until you get used to the system.

---

### Post by hatmancan on 2008-11-12
ok
trying not to be too stupid here but want to make sure before i do this..

i have the original ubuntu 8.04..
can i insert into the cd drive while still in windows and try to grab them?

or do i go and change the boot sequence to cd and ?? from there what??
hat

---

### Post by Steve1961 on 2008-11-12
You'll need to change the boot sequence so that the cd boots first.  You can't do it from windows.  once done you get a boot menu.  You want the first option which is something like 'try Ubuntu without installing'

---

### Post by hatmancan on 2008-11-12
ok..once i do that how do i transfer the files?
will i be able to move them into my windows from there?
i did have the wine program on there..
if i use the boot cd wouldn't i be able to explore file structure on my second hd? just like in windows?
there must be a way of transfering these files?
hat

---

### Post by Steve1961 on 2008-11-12
> **hatmancan said:**
> ok..once i do that how do i transfer the files?
will i be able to move them into my windows from there?
i did have the wine program on there..
if i use the boot cd wouldn't i be able to explore file structure on my second hd? just like in windows?
there must be a way of transfering these files?
hat

You do it as described in my earlier post.  Wine has nothing to do with this, you just grab your files and drop them in the place you want them.

---

### Post by hatmancan on 2008-11-12
steve
i booted with cd and got to see both hd's.
i created a folder on the windows hd and dragged folders into it.
some folders it would not let me as i did not have permission to.

also when i rebooted to windows the new folder is not showing???
any other suggestions?
ty
hat

---

### Post by Steve1961 on 2008-11-12
OK, two things to try.  It could be that you just don't have the correct permissions.  Open a terminal in the live cd and type gksu nautilus.  Then try copying and pasting the files again.

Second issue could be to do with whether ntfs rw is enabled on the live cd.  I was under the impression that it was, but if you still have issues try following this forum thread:

[http://ubuntuforums.org/showthread.php?t=542702](http://ubuntuforums.org/showthread.php?t=542702)

---

### Post by hatmancan on 2008-11-12
ok will try that next

out of curiosity would i not be able to update using my live cd???
if so how do i do that?
couldn't i use something like sudo apt-get update?
i found these things on some other problems and thought if i can use the live cd would be easier then switching back and forth everytime.
--i do beleive my big problem is the xserver-xorg
when i ran a reconfigure one time it would not let me..
are you able to troubleshoot anything there?
hat

---

### Post by Steve1961 on 2008-11-12
> **hatmancan said:**
> ok will try that next

out of curiosity would i not be able to update using my live cd???
if so how do i do that?
couldn't i use something like sudo apt-get update?
i found these things on some other problems and thought if i can use the live cd would be easier then switching back and forth everytime.
--i do beleive my big problem is the xserver-xorg
when i ran a reconfigure one time it would not let me..
are you able to troubleshoot anything there?
hat

As the live cd contains the same programmes that were used at installation there's no updated programmes on it.  If the main problem is an x server problem, you need to open a specific thread for that to make sure you get all the expertise available.

---

### Post by hatmancan on 2008-11-12
i tried with nautilus but would not work..
do you have any other suggestions i can use?

---

### Post by Steve1961 on 2008-11-13
Hmmm, I just tried using the live cd to see if I could save files to my xp partition, and it worked without a problem.  All I can suggest then is save the files to a usb stick or cd instead.

---

### Post by sirebral on 2008-11-13
You should be able to just mount the other HDs.  Then you can access you files and transfer them.

I was just curious if you could not mount the HDs.

---

### Post by IrishAndi on 2008-11-13
Hello there,

I personally dual boot between linux and XP as well and found a program that can read linux files under XP - there are a few, and even ones to "mount" them under your XP so you can access them as any other drive - but I never did that, because I didn't like the idea of something accessing my linux...

Anyway, the program I use, you can find it here

[http://www.diskinternals.com/download/Linux_Reader.exe](http://www.diskinternals.com/download/Linux_Reader.exe)

Hope that will help you solve your problem. You install it and you can only use it to copy stuff from your linux disk.

Good success! :)
God bless
Andreas

---

### Post by hatmancan on 2008-11-13
thanks to both of you.i downloaded the suggested link.. i see 2 physical drives..
under hard disk drives i see
c: 2 of them
h:1
1 linux native volume
1 linux swap
1 unallocated space(wdc_37gb at end)596.60mb

i think i have tooooo many drives.
i am just not sure what to do from here..
i am new to this so i think when i downloaded these desktops i somehow added these to hd's
is there a way to merge all these drives together without losing data?
or should i burn all to a cd and then reinstall everything??/
if so can someone give me some step by step to do this..
i have evolution mail and need to get into this to retrieve my emails
ty all again
await response
hat

---

### Post by hatmancan on 2008-11-13
> **hatmancan said:**
> thanks to both of you.i downloaded the suggested link.. i see 2 physical drives..
under hard disk drives i see
c: 2 of them
h:1
1 linux native volume
1 linux swap
1 unallocated space(wdc_37gb at end)596.60mb

i think i have tooooo many drives.
i am just not sure what to do from here..
i am new to this so i think when i downloaded these desktops i somehow added these to hd's
is there a way to merge all these drives together without losing data?
or should i burn all to a cd and then reinstall everything??/
if so can someone give me some step by step to do this..
i have evolution mail and need to get into this to retrieve my emails
ty all again
await response
hat

i was able to log into windows and i used my computer.i highlighted my h drive and was able to find some of my files there.i copied and pasted via this method and checked to see if they worked.
now if i could figure out how to retrieve my emails from evolution along with contacts?

has anyone any suggestions on how to repair my second drive where i have my ubuntu,kubuntu and desktops installed..
can i configure them from windows and if so how?
ty
hat

---

