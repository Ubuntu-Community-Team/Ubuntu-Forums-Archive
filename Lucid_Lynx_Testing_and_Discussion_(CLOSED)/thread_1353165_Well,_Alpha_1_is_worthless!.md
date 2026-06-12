---
title: "Well, Alpha 1 is worthless!"
date: 2009-12-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by theozzlives on 2009-12-12
I try to access my shares in the SAME workgroup and it asks me for a password. I've NEVER heard of a workgroup password!? Well, I try every password being used on the network, and none work. PERIOD! So so far Lucid is worthless to me without network access. We'll see if they get it fixed. :(

---

### Post by philinux on 2009-12-12
> **theozzlives said:**
> I try to access my shares in the SAME workgroup and it asks me for a password. I've NEVER heard of a workgroup password!? Well, I try every password being used on the network, and none work. PERIOD! So so far Lucid is worthless to me without network access. We'll see if they get it fixed. :(

Alpha 1 now let me think.... will all things work, will there be bugs and breakage?

No brainer init.

---

### Post by waspbr on 2009-12-12
^^^^

---

### Post by JT9161 on 2009-12-12
An Alpha not working properly ? I am shocked and outraged, this must not stand !

---

### Post by ranch hand on 2009-12-12
> **JT9161 said:**
> An Alpha not working properly ? I am shocked and outraged, this must not stand !
+1

Time now for a rant on how this is bad for Ubuntu's image but I am just not up to it today.

---

### Post by autocrosser on 2009-12-12
LOL----OLD story.........On a 1-to-10 scale the inverse of the alpha number is the possible b0rkage level....................

---

### Post by Gina on 2009-12-12
Works with ATI graphics - doesn't work with nVidia graphics!  There ya go!

Later I'll try it on my old Sapphire S3 :lolflag:

Previously, we've had complaints about nothing breaking!!!  On earlier versions.  No such complaints now!

---

### Post by theozzlives on 2009-12-12
I'm not saying it wasn't gonna break! Having it break early beats coming out with a release like Karmic. Anyhoo, it's in a VirtualBox so no harm done.

---

### Post by clivejo on 2009-12-12
It does work with nVidia graphics, try looking on their website.  Ask google !!

With all development software it is prone to problems, but that's the fun in being a tester.  If you want stable use Karmic !

I'm pretty impressed so far, and there is 4 months of hard work to go, so come on Ubuntu and make Lynx the best ever!!

PS My new laptop came with Windows 7 and I've formatted and installed Ubuntu 10.04, am I crazy?

Well too late now, I'm going to sit back and enjoy the ride :popcorn:

---

### Post by clivejo on 2009-12-12
Regarding the shares, do the user accounts match on each of the two machines ie both have a matching user account with same username and passwords?

If they don't it will ask you for a password.

---

### Post by waspbr on 2009-12-12
to be fair the nvidia drivers do work, just not the nooby friendly 185 ones, just the non-nooby friendly 195.22 beta...

---

### Post by scradock on 2009-12-12
> **theozzlives said:**
> I try to access my shares in the SAME workgroup and it asks me for a password. I've NEVER heard of a workgroup password!? Well, I try every password being used on the network, and none work. PERIOD! So so far Lucid is worthless to me without network access. We'll see if they get it fixed. :(
This was happening for me before the alpha-1 release - launchpad bug #490201.

Not only does the smb://workgroup/ fail to open in Nautilus, but it cannot be accessed using other methods like gvfs-mount smb://workgroup, so it's not just a Nautilus problem.

Even worse, the available methods for re-setting the password, or setting a NULL password, don't work in Lucid, though they seem to in karmic. "system-config-samba" won't change the password, and "sudo smbpasswd -n [USER]" doesn't do it either.

---

### Post by SuperSonic4 on 2009-12-12
> **theozzlives said:**
> I try to access my shares in the SAME workgroup and it asks me for a password. I've NEVER heard of a workgroup password!? Well, I try every password being used on the network, and none work. PERIOD! So so far Lucid is worthless to me without network access. We'll see if they get it fixed. :(

Something not working can be as important as something working - but only if a bug-report is filed

> **waspbr said:**
> to be fair the nvidia drivers do work, just not the nooby friendly 185 ones, just the non-nooby friendly 195.22 beta...

Can't you just grab them from nvidia and install from a tty?

---

### Post by louieb on 2009-12-12
Fresh install on desktop - SOS display problem since v6.06 Dapper. Same old fix too - had to build an xorg.conf with modlines and refresh rates to fit my Acer Display. Right now using the open source "nv" nvidia display driver. Going to switch to the nvidia 173 driver later and see if visual effects work.   

@ranch hand -  Really been a great time waste - kinda like feeding drinks to a :rolleyes: "Lounge Lizard":twisted:

---

### Post by Tonelero on 2009-12-12
> **Gina said:**
> Works with ATI graphics - doesn't work with nVidia graphics!  There ya go!


I have an ATI 4890 and the driver didn't install using the restricted drivers option. How did you get it to work?

---

### Post by phillw on 2009-12-12
So far, so good - I've only borked it the once.

I might register a bug, tho'. In previous incarnations of Ubuntu, my volume always played at about the equivalent of 50% in Win. -- Hmmm - Just had all the ear-wax cleared out of my ears & scared the cat - lol

Now, that's kewl :D

Phill.

---

### Post by jerrylamos on 2009-12-12
50-50 for me.  On the IBM ThinkCentre i845 graphics the 2.6.32-7 kernel locks up the gdm after just a few minutes.  Works O.K. with 2.6.32-5.

The Compaq ati graphics is working O.K. with 2.6.32-7.  So far...

Jerry

---

### Post by phillw on 2009-12-12
Well, this is deffo a bug - lmfao

[FONT=arial]sudo  tasksel

What ???!! - You mean you can just select what you want and it goes and gets it -- tsk, tsk - How are the 'gurus' supposed to make living if installing a LAMP server is *THAT * easy ???!!!

Darn, it works, as well. Wish I knew that command when I 1st installed LAMP under 9.04

It'll be offering to install cloud computing, samba services, mail servers & printer servers next .......

OMFG - It already does.
Quick - get it removed from options ;)

Phill.
(I can see wanting a larger hard-drive to 'play' with some of that stuff)
[/FONT]

---

### Post by Gina on 2009-12-12
> **Tonelero said:**
> I have an ATI 4890 and the driver didn't install using the restricted drivers option. How did you get it to work?It booted to CLI as usual, then I logged in and typed **startx** and the GUI worked.  I did tell it not to add "quiet splash" to the boot line during the installation (Alternate CD).

---

### Post by caryb on 2009-12-12
For Alpha 1 I only have broken wireless in Kubuntu I would consider that good going! This post would get some "slight" sympathy from me at final beta or at RC level

---

### Post by donniezazen on 2009-12-12
I am not a tech guy but we shouldn't be pessimistic as it is the first release.

Two problems that i faced were manual partition and NVIDIA driver. Work around worked in both cases.
:popcorn:

---

### Post by cariboo on 2009-12-12
> **scradock said:**
> This was happening for me before the alpha-1 release - launchpad bug #490201.

Not only does the smb://workgroup/ fail to open in Nautilus, but it cannot be accessed using other methods like gvfs-mount smb://workgroup, so it's not just a Nautilus problem.

Even worse, the available methods for re-setting the password, or setting a NULL password, don't work in Lucid, though they seem to in karmic. "system-config-samba" won't change the password, and "sudo smbpasswd -n [USER]" doesn't do it either.

```
smb://<servername>
``` 

does work providing you enter the username and password you use on the server. My server is running Jaunty server version, I don't know if that has anything to do with it. I only have Samba installed so the 2 Windows only computers on the network can use the shares. For the 5 Ubuntu systems, I use nfs, which works perfectly.

---

### Post by garvinrick4 on 2009-12-12
It is a bug in Lucid not with Samba they say but with Nautilus. I upgraded a little while
back and have home network. Cannot seem to find bug # but give it a google or look
on launchpad. It has to do with the password and Nautilus remaking new password everytime. 490201 that is the bug #. Give it a read in launchpad.

---

### Post by Regenweald on 2009-12-13
> **theozzlives said:**
> I try to access my shares in the SAME workgroup and it asks me for a password. I've NEVER heard of a workgroup password!? Well, I try every password being used on the network, and none work. PERIOD! So so far Lucid is worthless to me without network access. We'll see if they get it fixed. :(

You boys and girls must *really* give long hard thought about the manhours given by our developers to create this amazing free OS before you come up with thread titles. Good one guy.

---

### Post by ranch hand on 2009-12-13
Regenweald
What is up with you.  Are you trying to be a voice of reason?  What FUN is that?

Yes, as much as I hate too, I will admit to agreeing with you.

I get a kick out of it anyway remembering the thread from Karmic-testing about how the buggy alpha was going to give Ubuntu a bad rep.  I thought it was hilarious. 

But then, I do have a warped sense of humor.

---

### Post by VMC on 2009-12-13
> **Regenweald said:**
> You boys and girls must *really* give long hard thought about the manhours given by our developers to create this amazing free OS before you come up with thread titles. Good one guy.

True. Not a good way to get help. I often wonder what the devs think of these type of topics. 

There's a better way for asking for help instead of complaining.

---

### Post by ronacc on 2009-12-13
Testers are not "the public" the purpose of testing is to find and clearup these glitches before they get to "the public"

---

### Post by theozzlives on 2009-12-13
I was simply stating that Alpha 1 is not ready for me to test on any worth while machine (where it would get used), neither was Alpha 1 of Jaunty but you see how good it came out. I can access my shares if I type```
smb://192.168.1.x
```whatever the machine is. 

At least I can do that, with Karmic, I have to start SAMBA manually.

Also, I shop at the Ubuntu Store to help in the development. How many can say that? I wear my shirts and hat with pride and try to encourage the use of Ubuntu and Open Source when I can.

Will the graphics posters get your own thread?

---

### Post by terry_gardener on 2009-12-13
i have also had this problem but i have worked around the problem. 

if i clicked places-network and try to drill down to the share to my NAS then when i get so far i get asked for password. 

so i tried another solution to the problem. 

clicked places-connect to server, changed service type to windows share, typed in the ip address of NAS and then the name of the root folder i wanted to access ie public. 

clicked connect and it came up to save doing this each time i click bookmarks and add bookmark then when i want to open it i click places and the bookmark i created.

---

### Post by ranch hand on 2009-12-13
> **terry_gardener said:**
> i have also had this problem but i have worked around the problem. 

if i clicked places-network and try to drill down to the share to my NAS then when i get so far i get asked for password. 

so i tried another solution to the problem. 

clicked places-connect to server, changed service type to windows share, typed in the ip address of NAS and then the name of the root folder i wanted to access ie public. 

clicked connect and it came up to save doing this each time i click bookmarks and add bookmark then when i want to open it i click places and the bookmark i created.
I do not allow MS products in this house or to network from anywhere with my box.

That said,  I really like your thinking.  Nice work around.

For that matter, just NICE WORK.

---

### Post by 23meg on 2009-12-13
This thread has obviously been started in a specific way to provoke reactions, so I'm closing it. 

If you have a problem that you want to sort out, and/or need help with reporting a bug about it or fixing it for good, **start an appropriately titled thread** and ask for help. That's what this forum is mainly for. Opining on the relative "value" of milestones in and of themselves with a provocative tone, with no specifics and no tendency to help make things better is not what it's for, and won't be welcome. If you want to make future milestones more "ready to test" for yourself and everyone else, you may want to[ participate in ISO testing]("http://ubuntuforums.org/showthread.php?t=1347260") during the next freeze.

---

