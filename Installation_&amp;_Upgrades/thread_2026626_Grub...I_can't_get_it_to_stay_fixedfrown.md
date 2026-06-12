---
title: "Grub...I can't get it to stay fixed:frown:"
date: 2012-07-15
forum: Installation &amp; Upgrades
---

### Post by smcrossman on 2012-07-15
I've done 3 installs in the last 2 weeks.  First my system corrupted & I re-installed 11.40; Then due to outside software issues I decided to upgrade to 12.04.  First one suddenly decided to refuse to let anyone open anything in my home folder/directory. Since most things wouldn't install due to file conflicts and such I decided to do a merging of all those partitions and re-partition and install.  It's now working BUT suddenly I go into Grub Rescue every time I boot up.

I've researched and pretty much have the code memorized to get out to the menu.  When I get into Ubuntu proper I open a shell and do the ```
sudo update-grub
``` command. I now go thorough a long process of confirming where & what the grub files are & contain.  But if I try to reboot or shut down and start it up later I'm right back to grub-rescue .

The documentation I've been using is:
[https://help.ubuntu.com/community/Grub 2]("https://help.ubuntu.com/community/Grub 2") 
Mostly I'm using page 6 the grub rescue section. 

I'm starting to think it might be easier to make a boot disk or a "grub mkrescue" disk but before taking on something new I though I'd see if there was something I'm missing or ? 

This is on my 64bit system with Nvidia & GEForce everything which means that every install puts me to struggling to get to the menu which I can't do until the NVidia drivr is installed,...etc, etc, etc I'm also dual boot so that could be part of my problem here.

---

### Post by darkod on 2012-07-15
So, let me see if I understand this right: after the initial grub rescue, you know how to boot your ubuntu on the hdd?

In that case, the first thing to run is not update-grub, it's:
sudo grub-install /dev/sda

If you have more than one hdd, it might not be /dev/sda depending from which hdd you are booting.

That should reinstall grub2 to the MBR of the sda disk.

To double check how is grub2 configured, after that you can run:
sudo dpkg-reconfigure grub-pc

Only /dev/sda should be marked, if that's where you want your grub2. If it's not, select it with Space. Deselect all other locations that might be selected.

That should reconfigure it if somehow it was disconfigured.

---

### Post by jmfal on 2012-07-15
read up on it , make sure all references to grub2 are "grubpc

---

### Post by drs305 on 2012-07-15
If you install Boot Repair it should be able to analyze and repair the boot files. If not run the boot info script and post the results.  

Link is in my signature line.

---

### Post by smcrossman on 2012-07-15
Thanks for the responses! I've been trying to get some things done (like the the NSA back online & accessible); I'm shortcutting and doing multiple responses in one post.

1)I can repair grub to get into normal boot menu. Frrom there I can start up ubuntu, windows or go into recovery or memory checks.

Unfortunately my boot/grub is on my / partition. I've been trying to find another but it isn't there (3 installs ago I had a /boot partition LOL) So if I try to install grub I get the error message which which denies the command.

2) I can LOOK at grub.cfg and verify that it lists the prefix, /root, etc correctly (beyond that I don't know enough to troubleshoot the file) before shutting down or rebooting, but each startup ends up back at grub-rescue.

3)THat problem seems to be that it is using (hd0,5) for boot/grub and for root; The actual partition is (hd0,6) (i have 2 partitions & 1 swap for linux; they are on an extended partition  while the Windows and "system" recovery or the first ones on the HD

------------------------------

I've tried the grub-install but was getting error messages and no such device. I'll check it out again going for dev/sda which is of course where the natural boot record is.

----------------------

grubpc vs grub vs grub2;  Okay I sorted through the documentation for the most recently reviewed/updated (no promises I know.....but at least there shouldn't be anything blatantly 5 years old left in it)  I also carefully watched for what referred to grub or grub 1 to then be upgraded to grub2.  I also verified that I had grub.cfg; etc/default/grub installed; The fist page of the large document I listed actually goes through the installation process. So my understanding is that grubpc is used for the commands now, and that although everything is actually labelled grub the actual version classifies it as grub2.

-----------------------

I haven't looked at Boot Repair for this yet. I used to use Startup Manager for the NVidia issue. I tried Boot Repair with no results with the NVidia issue when Startup Manager became unavailable. I might want to re-examine it because I've hit the limit of my understanding and time for this.

---

### Post by drs305 on 2012-07-15
If you are having problems understanding the Grub community documentation I'm the one probably to blame. So if you don't understand it just ask - if it isn't clear to you there will be lots of others as well who are in the same situation.

I'd still recommend you install and run Boot Repair, and if it can't fix it post the contents of the script. Then we will really know what we are dealing with.

As *darkod* indicated, your Grub could be booting from the wrong device. Do you happen to have more than one drive and/or more than one version of Ubuntu installed?

The "grub-install /dev/sdX" should make sure the correct drive has the directions to the GRUB files. "update-grub" should update the grub files on your currently running OS. Of course, if the MBR is pointing to Grub files on another partition (an older partition) the correct files won't be updated with this command.

Here are two things you can do temporarily. Edit grub (gksu gedit /boot/grub/grub.cfg). Make a change in the title of the first entry (change something between the quotation marks). Save the file, but do NOT update-grub (or the changes may be erased). The next time you boot, see if the title reflects the change you made.

When you make the corrections so it will properly boot, are you only changing items in the Grub menuentry? If so, for now, copy the entire contents of the single menuentry and paste them below the existing lines in /etc/grub.d/40_custom. Edit the entry the same way you do from the Grub menu when booting. Save the file and then run update-grub. That should add the revised entry to the bottom of the existing menu items and the edited version should be available when you boot *if* this is the grub menu actually being used.

For efficiency, you could do the second step, save and update-grub, then do the menu title edit of the previous paragraph. Do not update-grub a second time. In this case, you should have the edited menuentry title *and* the 40_custom menuentry at the bottom. 

This should help booting until we can figure out what is going on.

Also,  you really shouldn't need a separate boot partition unless your BIOS has a drive read limit (normally these days 137GB) or you are using a special partitioning format other than BIOS/MBR.

---

### Post by smcrossman on 2012-07-16
Well due to the situation, I did go to install Boot Repair. Man I must have really been out of it because it took 3 tries to cut & paste the commands and get it to work. Then of course it RAN which I wasn't expecting. I looked at each screen, couldn't see anything any more dangerous than me playing with it all on my own, so I ran it.

My system boots up fine now. I did confirm (this morning) that I am getting my boot menu to access Windows. Oddly enough I now also can use my number keypad which was driving me crazy being inaccessible before.

What I didn't have it do was remove the original grub files from my / partition.  Although it is all in the MBR now, should I go back through or re-run the program to remove those old files?  Oh and basically I told it to use my existing etc/default/grub so my settings would all remain the same (therefore no resolution issues).

I remember back shortly after I started using Ubuntu (18 months ago) having grubrescue issues that I just could NOT figure out and even support was over my head. The documentation is so much better now with the step by step and explanations of different levels. 

Now I get to focus on preparing my place for inspection on Weds. Thanks for your help all!

Recommendations on dealing with the old files would be appreciated but I probably won't get back to report until later in the week.

---

### Post by drs305 on 2012-07-16
If things are working I'd leave the 'old files' as they are for now. For one reason, I'm not totally sure which files you are referring to - they could be the actual Grub files being used.

When Grub 'installs' to the MBR, as far as the MBR goes it places a smalll amount of information there telling BIOS where the Grub files actually reside. So your Grub files for the most part are in your /boot folder (normally /boot/grub).

Good luck with your inspection and happy Ubunut-ing !

P.S. Once you have your questions fully resolved, would you please mark the thread SOLVED via the 'Thread Tools' link near the top right of the first post. It helps us concentrate on unresolved issues and points those seeking answers to threads with solutions.

---

### Post by smcrossman on 2012-07-20
Promised to check back in. Took a little longer than planned.

Anyway....pc is booting fine. Menu and load up is much faster. Actually its all faster. So whatever I had wrong went further than just grub.

I agree that not messing with what works is a good thing in this case. Especially since those grub files might very well be the active ones....I had forgotten about the fact that they often end up in /boot rather than on the boot sector.

Thanks for all the help & have a great weekend!

---

### Post by drs305 on 2012-07-20
Thank you for the update.

Happy Ubuntu-ing !

---

