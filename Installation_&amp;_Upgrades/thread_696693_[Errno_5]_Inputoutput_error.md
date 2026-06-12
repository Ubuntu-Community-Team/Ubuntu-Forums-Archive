---
title: "[Errno 5] Input/output error"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by Slorg on 2008-02-14
I decided to dualboot my system again because of the lack of games (altough, I have 5 windows computers around me from other members of my family).

But when I tried to install Ubuntu I got the "Errno 5 input ouput error" message.
After a lot of cd's I decided it was hopeless

Now I try to install kubuntu again (I Prefer Kubuntu over Ubuntu), but it keeps giving me this error over and over again.
It's not my cd writer, I tried it with my dad's mine and one the one of the pc in the living room but nothing works.

I formatted my drive several times but it doesn't work.
Then I downloaded the alternate cd, and burned it.
Then I checked the CD for defects and it gave an error (1 .DEB file is damaged)
But my live cd's where just fine.

I'm now downloading the alternate cd but after weeks of trying installing ubuntu ( I had this issue before, never solved it, it just seemed to work sometimes on a mysterioucly way) I don't have many hope left. 

(downloading a single cd costs 2 hours here, I'm now downloading the third alternate Kubuntu cd in 2 days (yesterday two, (one came with a 600 MB. part and a little .ISO but firefox DID say it's OK) (one with says 1 deb is damaged) this morning (someone of my family cancelled it, I don't know who yet but I'm gonna kill her :P ))

And when I partion or format my drive my computer often freezes (the caps- and scroll locks are turning on and off and on and off etc but the screen freezes).

I think the problem is: 
- Or my hard disk is damaged, but it is just a half a year old
- Or it is because my bios doesn't support my hard disk 100%, it says it has only 130 GB (It's an old motherboard from 2000 (Epox EP-3SPA3L)) And when I have dualboot with no boot partition in the beginning it's giving me a grub error (I don't remind the number anymore I thought around 20) 

I tried the following ways:
-Cleaning my CD writer/reader lens
-Cleaning my DVD reader lens
-Downloading new ISO
-Burning the ISO with 1x
-Formatting my drive
-Manually partition it and change the mount point on the install

I can't boot from USB, My mother board doesn't support it and it doesn't have any flash upgrades either
And I can't buy a new PC or mother board because I haven't money or a job (I'm busy enough with school and there aren't many paying jobs for 14 year olds ^^)

My specs:

- 128 MB ATI RADEON 9200 Video card
- 160 GB Western digital Hard disk
- DVD Rom reader
- CD Rom writer/reader
- 933 MHz
-  512 MB RAM
- Epox mother board (EP - 3SPA3L If i'm correct)

Can someone please give me a solution to this problem? (I don't want windows with it just Kubuntu 7.10)?

---

### Post by Slorg on 2008-02-15
Still no anwers?, Bump

Still have the same problem...

---

### Post by xeth_delta on 2008-02-15
Welcome to the forums!
What is the furthest you can get through installation with the alternate CD. BTW, I'm also a Kubuntu user.

---

### Post by Slorg on 2008-02-18
It's a few days later now and it still doesn't work.
I get an MD5 CHECKSUM MISMATCH error.
Altough it's a perfect cd, when I scan it for errors on the computer of my father it says it has no error.
But when I scan it for defects on my pc it gives the checksum error.

I don't think my dvd reader is damaged, I cleaned it yesterday with an CD Lense cleaner for 20 minutes but it didn't work.
And I did also put a vacuum cleaner on it to be sure there is no dust in it.
My reader is just a few months old and I didn't abuse it or something.
It is not a second hand, it is manufactured in October 2006 (I bought it somewhere 'round octobre 2007.
And for further details:

Sony NEC Optiarc Inc.
DVD-ROM DRIVE
MODEL DV-5800E

My CD writer also said it has errors when I tried to scan it.

I wrote it with my writer, it says it has errors.
And I also wrote it with the dvd writer of my father but It still has errors according to my readers.
But on the pc of my father it says it has no errors

Still haven't got any farther :(
Can someone please help?

edit:
And by the way, I tottally agree with your 'Say NO to software patents in the European Union!' 
The software patents are one of the biggest things I have against the EU (I live in holland by the way)

---

### Post by wpshooter on 2008-02-18
First can you tell me if the computer that you are having trouble with is one that you built or is it one that was purchased directly from some vendor ?

Second, do you know how the 2 CD/Optical drives are connected to the motherboard and how they are jumpered.

Also, is the Western Digital hard drive on a different controller/connector on the motherboard from the CD/Optical drives and is the hard drive jumpered as MASTER ?  Is the hard drive an IDE drive or a SATA drive ?

---

### Post by xeth_delta on 2008-02-18
> **Slorg said:**
> It's a few days later now and it still doesn't work.
I get an MD5 CHECKSUM MISMATCH error.
Altough it's a perfect cd, when I scan it for errors on the computer of my father it says it has no error.
But when I scan it for defects on my pc it gives the checksum error.

I don't think my dvd reader is damaged, I cleaned it yesterday with an CD Lense cleaner for 20 minutes but it didn't work.
And I did also put a vacuum cleaner on it to be sure there is no dust in it.
My reader is just a few months old and I didn't abuse it or something.
It is not a second hand, it is manufactured in October 2006 (I bought it somewhere 'round octobre 2007.
And for further details:

Sony NEC Optiarc Inc.
DVD-ROM DRIVE
MODEL DV-5800E

My CD writer also said it has errors when I tried to scan it.

I wrote it with my writer, it says it has errors.
And I also wrote it with the dvd writer of my father but It still has errors according to my readers.
But on the pc of my father it says it has no errors

Still haven't got any farther :(
Can someone please help?

edit:
And by the way, I tottally agree with your 'Say NO to software patents in the European Union!' 
The software patents are one of the biggest things I have against the EU (I live in holland by the way)

You may want to try checking the MD5 sum for the actual image you downloaded on your hard-disk. It might be corrupted and hence any cd you burn from it will have problems.
Have a look here: [https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28#head-6788e413b69a8947c263c08d435f3e7fa8a3237d](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28#head-6788e413b69a8947c263c08d435f3e7fa8a3237d)

About the software patents issue, I am glad people agree they are a really bad idea, thanks for your words. What these patents are achieving is to hinder innovation and are really becoming a nuissance for software developers, expecially independent or small ones.

---

### Post by Slorg on 2008-02-18
I don't think there's anything wrong with the image.
Because when I check it for errors on other computers it says there are no problems...
And I tried it with 3 differen images from 3 different servers and burnt a lot of them with 1x

[http://img134.imageshack.us/my.php?image=pict0004bq7.jpg](http://img134.imageshack.us/my.php?image=pict0004bq7.jpg)
Here an image of my burned ubuntu cd's to give you an image of how long I have this problem and try 
And another image showing the same cd's...
[http://img138.imageshack.us/img138/9712/pict0005to2.jpg](http://img138.imageshack.us/img138/9712/pict0005to2.jpg)

Yes there are some original cd's with it but they are all linux

Btw. The software patents will also give MS a change to use their patentstealing stuff FUD, and really sue linux users while MS is the king of  ripping of:mad:

---

### Post by xeth_delta on 2008-02-18
> **Slorg said:**
> I don't think there's anything wrong with the image.
Because when I check it for errors on other computers it says there are no problems...
And I tried it with 3 differen images from 3 different servers and burnt a lot of them with 1x

[http://img134.imageshack.us/my.php?image=pict0004bq7.jpg](http://img134.imageshack.us/my.php?image=pict0004bq7.jpg)
Here an image of my burned ubuntu cd's to give you an image of how long I have this problem and try 
And another image showing the same cd's...
[http://img138.imageshack.us/img138/9712/pict0005to2.jpg](http://img138.imageshack.us/img138/9712/pict0005to2.jpg)

Yes there are some original cd's with it but they are all linux

Btw. The software patents will also give MS a change to use their patentstealing stuff FUD, and really sue linux users while MS is the king of  ripping of:mad:

When exactly does the error appear? You could try to install the absolute minimum from the CD, then reboot from the minimal linux installation and connect to the internet. Then download and install from the repositories the rest of the software you will need. This is the tactic I used with a reticent computer of mine some time ago. It worked, and it has been working on Ubuntu without issues since.

A bit off topic again, in my view there are countries in which some big software corporations (I guess you know which) have been strongly lobbying for such patents, which would give them control (and much of a monopoly) over software development in a completely ilegitimate and unethical way. Because many laws are made by people, and as such, they are imperfect and can be sometimes wrong. Luckily in Europe we still don't have this utter non-sense implemented yet, and hopefully never will be.

---

### Post by Slorg on 2008-02-18
Ok, I used another cd reader this time.
And guess what? It doesn't work (again)
This is really driving me crazy
It stops at 19% of the CD Integrity test.

Can someone PLEASE help me?

---

### Post by xeth_delta on 2008-02-18
> **Slorg said:**
> Ok, I used another cd reader this time.
And guess what? It doesn't work (again)
This is really driving me crazy
It stops at 19% of the CD Integrity test.

Can someone PLEASE help me?

Please read my previous post and let me know.

---

### Post by Slorg on 2008-02-18
Yes I will try what you said, I guess it's the only thing that might work :(
I'll post the result when I'm finished

---

### Post by Slorg on 2008-02-19
Before I can install anything I have to do the base install.
Somewhere around 60 - 70 % it gives an error where I can't go any further only abort the installation (I get an error around 5% and another aroun 60% but I can go further.

Anyway when I now load kubuntu I get into the command prompt.
Then I type 'start x' and get into the graphical part.
But almost no program seems to work, I can't use konqueror so I can't use the internet.
Adept doesn't work either.

So I didn't get much farther, I really don't mind a clean install since nothing is installed anyway so can someone Please help me?

---

### Post by xeth_delta on 2008-02-19
> **Slorg said:**
> Before I can install anything I have to do the base install.
Somewhere around 60 - 70 % it gives an error where I can't go any further only abort the installation (I get an error around 5% and another aroun 60% but I can go further.

Anyway when I now load kubuntu I get into the command prompt.
Then I type 'start x' and get into the graphical part.
But almost no program seems to work, I can't use konqueror so I can't use the internet.
Adept doesn't work either.

So I didn't get much farther, I really don't mind a clean install since nothing is installed anyway so can someone Please help me?

Make sure the repositories are enabled. Stay in the command line environment and run
```
sudo apt-get clean
sudo apt-get update
sudo aptitude reinstall kubuntu-desktop
```

---

### Post by Slorg on 2008-02-19
Thank you for your patience and help.
But I finally solved it thanks to the dutch ubuntu forums.
The problem was my memory, I had 2* 128 and 1 * 512.
But my BIOS had problems with the 512 and read it as 256 because it is an old mediocre piece of crap.
Now I have 3 * 128 MB Ram but I can use linux.:guitar:
Thank you for your help.:)

---

### Post by Slorg on 2008-02-19
Erh how do you mark the topic as solved?

---

### Post by xeth_delta on 2008-02-19
Glad to learn it's working now. It seems sometimes we forget to check the most obvious possibilities. In this case memory issues. You know, if the module has some damaged memory addresses, you can tell the kernel not to use them. The rest of the module should work fine.

---

