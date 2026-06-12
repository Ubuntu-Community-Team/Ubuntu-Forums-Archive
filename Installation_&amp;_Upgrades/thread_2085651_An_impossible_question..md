---
title: "An impossible question."
date: 2012-11-18
forum: Installation &amp; Upgrades
---

### Post by djpython on 2012-11-18
I am installing ubuntu-secured-remix and then "mdadm" and then Postfix...

The Postfix installer asked me to choose the type of mail server configuration I needed. 
Now I dont understand why I need to send mail to fix my beyedoot record but, ...OK:

The smallish window gave me four or five choices and at the bottom of the window there was  <OK>

Now I clicked and dragged and right clicked on a hundred permutations of symbols on that window but nothing responded, ...at all.       wassupwiddat?

And, of course, there are no recognizeable controls, buttons ..., nothing.

Let me go look to see if there is another window lurking in the background.... Nope, none.   But I was reminded that this is in a terminal window? And that I am in a live cd environment.  Could that be a reason it cant do this little input fcn? 

Helllp.  Im 2-3 days dancing in and around thi s             .](*,)](*,)](*,)

You help will be greatly appreciated.     -djp

OK.  Maybe its because this is a live CD?  I am totally new to Linux, Ubuntu, etc...  Coulld the installer be blind to that?

---

### Post by darkod on 2012-11-18
If you are in a live session, how do you plan to install anything permanently? When you reboot the session is gone.

Don't you have an installed ubuntu to work with?

On another note, when you have a text menu, usually you move in it by using the arrows keys and TAB, and you make selections where needed with the Space bar. Like in a tick box or similar.

---

### Post by djpython on 2012-11-18
Hey, Darkod,

Thanks for the quick enjoinder.

But I should clarify.  I was hesitant to install U because there is  a dysfunctional Fedora there already and I am trying to save my data- like my browsing history and a few files.

I think U asks to format the partition and thats cooked then.

I am just hesitant in general.  I dont know what I did wrong to make 3 of 5 Fedora partitions become innaccessible.  But I do know that when the Boot It Bare Metal uninstalled gave me "complete, with errors" that my apprehension was justified. It had made things worse and now Mint Linux and Windows wont boot either.

About the text window-  I know what you mean.  But I have clicked on every mm^2
of that terminal window and I just CANT get the cursor to PLANT anywhere. The window with the prompt is NON-INTERACTIVE.

        Ill go check to see if I missed anything in that terminal window. After all, Im totally new to Linux and maybe I missed something.  Nope.  I cant get a cursor to plant.  I cant scroll.  No logical option anywhere with the right click.

         I have a newish HP dv7 with windows 7, Linux Mint and Fedora 13 installed and as of few days ago, working.  .


Thanks in Advance-  I am a total newb.  Like the whole Nononoosphere is a bunch of dead ends.

---

### Post by darkod on 2012-11-18
Hold on, is the operation saving data?

If it is, why would you install mdadm and postfix in a live session?

If you do have mdadm raid array then I can understand installing the mdadm package since the ubuntu live session doesn't have it.

But if it's fedora we are talking about, and you didn't use mdadm raid, fedora installs usually with LVM, which is different than mdadm raid.

You should install the lvm2 package and activate the volume group(s):
```
sudo apt-get install lvm2
sudo vgchange -ay
```

That should list the activated Logical Volumes. After that, they are present as:
/dev/VGname/LVname

You still have to mount them so you can read them, for example:
```
sudo mkdir /media/temp1
sudo mount /dev/VGname/LVname /media/temp1
```

After that they are present in /media/temp1 and it should also be visible in the file browser (Nautilus).

---

### Post by djpython on 2012-11-18
/Edit:  I dont think the boot repair installation is writing, but my Ubuntu install can write to an NTFS partition I have on the Windows disk.   

So guess the big moment will be when, after using lvm2, whether I will be able to boot.

Man, you are fast by the way. Phew. 

It seems I may or may not have a serious problem here.

I also want to get this repair boot to work as I am not such an advanced user, but I hope to keep hacking and someday be such and I may need that tool to keep-
 :guitar:   playing.                


   Do you suppose I can just quit the install at that point and say           "who cares about Postfix for now"?

Anyway, let me try what you say and Ill be back.

Thanks Again

---

### Post by djpython on 2012-11-22
I still dont have an answer to my (original) question:  What do i do to properly install mdadm and configure Postfix which are both asked for when I try to use boot-repair from (my now installed on the disk ubuntu-secure-remix).   I am afraid that u-b-r may goof if I just ignore this. (When I do it asks if I am sure and that I am quitting an ongoing process...)

BTW:  I couldnt get the boot-info summary from the other option.  I had to download a standalone bootinfoscript  (not boot-info-script*.sh either)  and that worked.

That choose screen is truly non-interactive so seems to be a bug.  Should i report it?

djp

---

### Post by darkod on 2012-11-23
I am still confused. :)

You say you have Fedora full of data that you don't want ubuntu to overwrite so you haven't installed ubuntu yet (although you might have done it meanwhile). But yet, you are trying to use ubuntu boot-repair to try and fix fedora boot? I don't think it can work on fedora, it's an ubuntu program.

As I asked before, and you failed to reply exactly, is the goal of the operation only to save the data from fedora and then overwrite it with ubuntu, or to repair the fedora boot and keep using it?

If you only want to read/copy the data from fedora, you don't need boot-repair. You can boot with the ubuntu live cd in a live session, do a few steps to recognize the LVM, and start copying data to some external hdd for example. Is that what you want to do?

To answer your question, NO, boot-repair shouldn't ask you for mdadm or postfix, it makes no sense. But if you are trying to use it on a fedora installation it might say things that don't make sense since it's not for fedora.

---

### Post by YannBuntu on 2012-11-24
Hello
Boot-Repair should be able to fix an installed Fedora, at least on basic cases.
It never asks to install postfix.
It can ask to install mdadm (when it detects "mapper" in blkid), but if you don't use RAID, you can safely ignore this.

---

