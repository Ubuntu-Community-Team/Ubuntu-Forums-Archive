---
title: "Safer way to upgrade?"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by gewitty on 2010-07-03
I'm currently still running 9.10, but would like to upgrade to 10.04. However, I currently have a very stable system with quite a lot of apps installed and previous experience of running upgrades from Update Manager have left me nervous, as they have sometimes broken my systems badly.

A while ago, I spotted this tip:

**Upgrading**

[I]If you reinstall over the top of an existing install, and during the partitioning step of the live cd installer choose manual partitioning and unselect the 'format' tickbox, magic happens. The installer will recursively delete all of the folders in / except /home. So that's /bin /usr /var /etc and so on. That all gets deleted and the new system gets installed, leaving /home alone.
[/I] 

Questions:

1) Does this actually work?
2) I assume that the reinstall is done using a CD?
3) Is this a safer way to upgrade than via Update Manager?
4) Will this method preserve all of my existing set-up and installed apps?
5) Is there a better way to ensure a safe upgrade?

---

### Post by dino99 on 2010-07-03
if you own a /home, all your data and settings are safe

you can either make a clean install with a cd/dvd/usb image, better to format before and choose custom installation to avoid grub overwritting unwanted other loader (windoz or osx if any)

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

or change "karmic" by "lucid" into synaptic repo, then update upgrade

---

### Post by gewitty on 2010-07-03
> **dino99 said:**
> if you own a /home, all your data and settings are safe

Does that go for all my installed programs as well? Are they still retained?

---

### Post by darkod on 2010-07-03
> **gewitty said:**
> Does that go for all my installed programs as well? Are they still retained?

Ignore that post, he didn't read your first post carefully. He thinks you have separate /home partition. If you format / all will be lost, including personal data.

I haven't tried it myself, but I have seen it here on the forum where people tried exactly what you described. Using the manual partitioning method, set the root partition to be used as root but untick the format box.
They claimed all went well, and even their personal data was saved. But I can't guarantee for every single program you have.
Maybe it also depends whether all your programs were installed with Synaptic or some of them manually.

If you can do it, one option is to make a clone of your / partition with Clonezilla for example, and then try the clean install without formatting /. If you are not happy how it went, just put back the backed up image.

---

### Post by gewitty on 2010-07-03
> **darkod said:**
> one option is to make a clone of your / partition with Clonezilla for example, and then try the clean install without formatting /. If you are not happy how it went, just put back the backed up image.

That's what got me out of trouble last time :p

When dealing with installed programs, does anything get stored in directories outside of those in 'Home'?

---

