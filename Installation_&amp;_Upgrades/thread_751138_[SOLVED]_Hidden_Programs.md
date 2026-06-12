---
title: "[SOLVED] Hidden Programs"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by anthony2010 on 2008-04-10
Hi all.

On occasion a downloaded program such as 'pspp' from cnr or another repository will install but be invisible to me. I cant find it anywhere yet it insists its installed. Ive had this before with a couple of applications and was wondering how I should go about rendering these programs useable.

Any ideas would be most welcome!

Thanks all.

Ant.

---

### Post by munkyeetr on 2008-04-10
Try using the **which** command to find where it was installed to:
```

which pspp

```

and try either running it either from the command line like so:
```

pspp &

```

or using the full path as shown in the which command above. These would be my first attempts.

---

### Post by anthony2010 on 2008-04-10
antman@SOS9000:~$ PSPP is free software and you are welcome to distribute copies of it
under certain conditions; type "show copying." to see the conditions.
There is ABSOLUTELY NO WARRANTY for PSPP; type "show warranty." for details.
GNU pspp 0.4.0 (Fri Mar  2 08:27:20 UTC 2007).
PSPP> 


This is what I got for the command pspp &.

I was hoping for a program not unlike spss that has buttons and twiddly bits I could navigate! Is there something I should enter after PSPP> ?

Thanks for the help!

ant.

---

### Post by munkyeetr on 2008-04-10
I don't know, it looks like a console program, though wiki says it also has a GUI.
Try typing:
```

help

```

but I really don't know the specifics of this program. Look through the [documentation]("http://www.gnu.org/software/pspp/") to get more information on how to use it.

---

### Post by mali2297 on 2008-04-10
I think the GUI refers to [PSPPIRE]("http://www.gnu.org/software/pspp/psppire.html"), which is *currently in alpha phase.*.

---

### Post by anthony2010 on 2008-04-10
Thanks both.

What I will do is wait until Pspp reaches beta. 

Regards

ant

---

### Post by S3Indiana on 2008-04-10
> **anthony2010 said:**
> On occasion a downloaded program such as 'pspp' from cnr or another repository will install but be invisible to me. I cant find it anywhere yet it insists its installed. Ive had this before with a couple of applications and was wondering how I should go about rendering these programs useable.For future reference: open the client, highlight the package, then right-click then select Files Associated providing locations of all the associated packages...

---

### Post by compiledkernel on 2008-04-11
Anthony, if indeed you are using CNR to install applications, CNR has their own provided website for support.

[http://www.cnr.com/supportPages/community.seam](http://www.cnr.com/supportPages/community.seam) -- Community Page
[http://support.cnr.com/support.jsp](http://support.cnr.com/support.jsp) -- Support Page.

Let me re-iterate the current forum policy on 3rd party package management and scripting applications --

[http://ubuntuforums.org/announcement.php?f=13/](http://ubuntuforums.org/announcement.php?f=13/)

CNR is not different than the applications listed, and if your seeking further support for the application use their venues , and surely you will receive a better avenue of support.

You should easily be able to find the root of your issues there mon ami. 

Cheers.

---

### Post by anthony2010 on 2008-04-11
Thank you for that! I wasn't aware there was a rule regarding the discussion of 3rd party software.

I will bear that in mind for the future!

I have another question which is an OS question: 

Know how in windows you can defragment your drive to get rid of old bits of files etc. Is there such a facility to clean up the drive under Ubuntu 7.10?

ant.

---

### Post by mali2297 on 2008-04-11
> **anthony2010 said:**
> 
Know how in windows you can defragment your drive to get rid of old bits of files etc. Is there such a facility to clean up the drive under Ubuntu 7.10?

Huh? I have a vague recollection of something like that when I used Windows, but that feels like a very long time ago.

The ext3 file system (which is the default in Ubuntu) does not have a defragmentation tool and frankly does not need one. See 
[http://en.wikipedia.org/wiki/Ext3#Defragmentation](http://en.wikipedia.org/wiki/Ext3#Defragmentation)

---

### Post by compiledkernel on 2008-04-11
There is no such animal in the unix linux world, largely becuase as mali has shown, fragmentation doesnt typically occur in such systems on the level that you would see in a windows machine.

---

### Post by anthony2010 on 2008-04-12
Thanks for that link martin. Pretty informative reading! I like how the ex3 format optimises disk space as it goes. Cool stuff! Pretty well thought out this ubuntu.

Thanks for all your help. Will mark this thread as solved.

---

