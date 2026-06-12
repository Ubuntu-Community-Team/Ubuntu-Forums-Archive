---
title: "Ubuntu 11.04.  How much disk space does it take up once it's installed?"
date: 2011-09-01
forum: Installation &amp; Upgrades
---

### Post by pretty_whistle on 2011-09-01
How much disk space does Ubuntu 11.04 take up once installed?

I don't know how to get this info myself other than ask here.

Does anyone know?

---

### Post by coffeecat on 2011-09-01
A default installation will be about 2.2 to 2.4 GB, but you'll need more hard disc space than that. I believe the 11.04 installer won't install to something less than 4GB - if I remember correctly.

How much space were you thinking of making the Ubuntu root partition?

---

### Post by pretty_whistle on 2011-09-01
> **coffeecat said:**
> A default installation will be about 2.2 to 2.4 GB, but you'll need more hard disc space than that. I believe the 11.04 installer won't install to something less than 4GB - if I remember correctly.

How much space were you thinking of making the Ubuntu root partition?

I forgot to say it's already installed.  Windows 7 used to be there but I replaced it with Ubuntu 11.04.

I installed it off the CD and Ubuntu is all I have on the hard drive period.  My HDD  is 160GB.

I'm just wondering how much it takes up now that it's there.

---

### Post by coffeecat on 2011-09-01
> **pretty_whistle said:**
> 
I'm just wondering how much it takes up now that it's there.

Open System Monitor. (System menu in classic gnome, or from the shutdown button -> System Settings in Unity). Click on the File Systems tab. That will give you the size and usage of each of your mounted partitions.

---

### Post by pretty_whistle on 2011-09-01
> **coffeecat said:**
> Open System Monitor. (System menu in classic gnome, or from the shutdown button -> System Settings in Unity). Click on the File Systems tab. That will give you the size and usage of each of your mounted partitions.


Here's what it shows:

[IMG]http://i54.tinypic.com/dpd74w.png[/IMG]


It shows 126.3GB used.  I presume the operating system itself isn't that big, or is it?

---

### Post by haqking on 2011-09-01
> **pretty_whistle said:**
> Here's what it shows:

[IMG]http://i54.tinypic.com/dpd74w.png[/IMG]


It shows 126.3GB used.  I presume the operating system itself isn't that big, or is it?

When you say Windows 7 used to be on there, how did you remove it ?

is this a fresh install or you been using it for a while

---

### Post by pretty_whistle on 2011-09-01
> **haqking said:**
> When you say Windows 7 used to be on there, how did you remove it ?

is this a fresh install or you been using it for a while


I booted with the Ubuntu CD and hit 'install'.  When done, Windows 7 was gone and Ubuntu was there.

I did this about 5-6 days ago.

---

### Post by haqking on 2011-09-01
> **pretty_whistle said:**
> I booted with the Ubuntu CD and hit 'install'.  When done, Windows 7 was gone and Ubuntu was there.

I did this about 5-6 days ago.

I am thinking that the Windows directory and its files are still there possibly.

Or you have downloaded lots of files in the last 5-6 days ;-)

---

### Post by pretty_whistle on 2011-09-01
> **haqking said:**
> I am thinking that the Windows directory and its files are still there possibly.

Or you have downloaded lots of files in the last 5-6 days ;-)

Well, I certainly haven't downloaded lots of files.  :)

I have a boot CD and I could use that and see if anything besides Ubuntu is on there.  It has various utilities and a Windows-like explorer on it so I can see.

I'm wondering something.  Earlier I tried to make a clone backup and did it wrong.  It never got saved to the portable hard drive and I had wondered if by accident it got saved onto Ubuntu somewhere.  But the question is WHERE.  I wonder if that's where the space went.  How can I look for that though...

---

### Post by haqking on 2011-09-01
> **pretty_whistle said:**
> Well, I certainly haven't downloaded lots of files.  :)

I have a boot CD and I could use that and see if anything besides Ubuntu is on there.  It has various utilities and a Windows-like explorer on it so I can see.

why do you need to do that, just browse your / with nautilus.

See if anything like a windows directory is there or any folders from your previous installation

---

### Post by saltmarshlamb on 2011-09-01
Open a terminal 

run ```
baobab
```

scan filesystem

should tell you quite a lot :)


[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

---

### Post by westie457 on 2011-09-01
Hi.

Try using 'Disk Usage Analyser' that should show where the biggest files are. 

If that shows nothing is using or causing the lost space I would advise you to boot into a Live Desktop start Gparted and run a File System Check from there.

This worked for me after I 'lost' 90% of the free-space on my hard drive.

---

### Post by pretty_whistle on 2011-09-01
> **haqking said:**
> why do you need to do that, just browse your / with nautilus.

See if anything like a windows directory is there or any folders from your previous installation

Did you see what I edited above?  It was this part:

"I'm wondering something.  Earlier I tried to make a clone backup and did  it wrong.  It never got saved to the portable hard drive and I had  wondered if by accident it got saved onto Ubuntu somewhere.  But the  question is WHERE.  I wonder if that's where the space went.  How can I  look for that though..."

I think this may the issue but I don't know for sure, a clone sitting where it shouldn't be.

---

### Post by haqking on 2011-09-01
> **pretty_whistle said:**
> Did you see what I edited above?  It was this part:

"I'm wondering something.  Earlier I tried to make a clone backup and did  it wrong.  It never got saved to the portable hard drive and I had  wondered if by accident it got saved onto Ubuntu somewhere.  But the  question is WHERE.  I wonder if that's where the space went.  How can I  look for that though..."

I think this may the issue but I don't know for sure, a clone sitting where it shouldn't be.


ahh yes could well possibly be.

Good suggestions above should find the issue.

---

### Post by pretty_whistle on 2011-09-01
Aha!  I've found it.  The clone is and taking up 122GB of space!

But it won't let me delete it!

How do I delete it?

---

### Post by saltmarshlamb on 2011-09-01
Open a file broswer as root - be very careful you don't delete anything you shouldn't though.

```
gksudo nautilus
```

Just in case you didn't know - the baobab I referred to is in fact the same thing as westie457's disk analyzer - I assumed you to be using unity and I have absolutely no idea how to use that or find it - so running the command from a terminal got past my lack of knowledge :)

---

### Post by coffeecat on 2011-09-01
@pretty_whistle, if you use a "gksudo nautilus" file browser as saltmarshlamb suggests, you need to beware of one thing. If you use the delete key, it will simply move the clone file(s) to root's trash. It will still be taking up room on the hard drive, simply in a different folder.

Use the shift+delete key combination. That will prompt you with an "are you sure?" but will physically remove the file(s) you want to delete. But as saltmarshlamb quite rightly says: be careful. You have full root privileges with a gksudo nautilus file browser window.

Alternatively you can use "sudo rm" from the terminal. If you want help with that post back with details of where you found the clone.

---

### Post by pretty_whistle on 2011-09-01
> **saltmarshlamb said:**
> Open a file broswer as root - be very careful you don't delete anything you shouldn't though.

```
gksudo nautilus
```Just in case you didn't know - the baobab I referred to is in fact the same thing as westie457's disk analyzer - I assumed you to be using unity and I have absolutely no idea how to use that or find it - so running the command from a terminal got past my lack of knowledge :)

I deleted it using that, thanks.

But the disk use is still the same.  What the...?

The clone I just deleted said it was 122GB, so how can this be?  WEIRD.

---

### Post by haqking on 2011-09-01
> **pretty_whistle said:**
> I deleted it using that, thanks.

But the disk use is still the same.  What the...?

The clone I just deleted said it was 122GB, so how can this be?  WEIRD.

empty the trash

---

### Post by coffeecat on 2011-09-01
> **pretty_whistle said:**
> 
The clone I just deleted said it was 122GB, so how can this be?  WEIRD.

**Read my post #17.** The clone is now in root's trash.

---

### Post by pretty_whistle on 2011-09-01
I emptied the trash.  Go figure it didn't help.

---

### Post by saltmarshlamb on 2011-09-01
Root's trash is not in your normal trash :)

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

Should be here - ```
gksudo nautilus /root/.local/share/Trash
```

---

### Post by pretty_whistle on 2011-09-01
> **saltmarshlamb said:**
> Root's trash is not in your normal trash :)

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

Should be here - ```
gksudo nautilus /root/.local/share/Trash
```

Aha!  My free space has been found!  So THAT'S where you were <talking to my free space....>

It WAS that darn clone after all but in root's trash!

Thanks.  That solved it.

---

