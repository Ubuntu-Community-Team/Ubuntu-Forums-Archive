---
title: "How do i file a bug against the ubuntu installer"
date: 2014-07-25
forum: Installation &amp; Upgrades
---

### Post by dandandan on 2014-07-25
I am to stupid to find it, please advise.

---

### Post by kansasnoob on 2014-07-25
If it's the live installer:

```
ubuntu-bug ubiquity
```

What's the bug?

---

### Post by dandandan on 2014-07-26
No idea what the live installer is, the thingie that installs Ubuntu on your hdd when you boot with cd/usb stick.
Its not a Bug but a problem, the installer asks for the wlan password on laptops before it sets keyboard layout. Non tech ppl will give up at this point already since they might be unable to enter their wlan password.

---

### Post by Lars Noodén on 2014-07-26
That would be Ubiquity, if it is the graphical installer.  When you get to that part of the installation press ctrl-alt-T to bring up a terminal and then enter 'ubuntu-bug ubiquity' as mentioned.  That will collect all the pertinent information about the version you are using and automatically add that to the bug report.  Of course you still have to write a description.

Have you checked Lauchpad to see if the bug has been reported already?

---

### Post by dandandan on 2014-07-26
Thank you. I have not checked before, launchpad ui usability is horrible for finding stuff, or i am way too stupid to use it, 50/50 chance :)

---

### Post by coffeecat on 2014-07-26
> **dandandan said:**
> 
Its not a Bug but a problem, the installer asks for the wlan password on laptops before it sets keyboard layout. Non tech ppl will give up at this point already since they might be unable to enter their wlan password.

Not just laptops - desktops with wi-fi too.

You would be wasting yours and the developers' time by reporting this non-existent problem. On the installer page where you can connect to a wi-fi network and set the wi-fi password, there are two radio buttons to make a choice between:

"I don't want to connect to a wi-fi network right now"

and

"Connect to this network".

Followed by a list of detectable wi-fi networks and a field for the password.

I'm sure most non-tech people who don't have the password to a wi-fi network can work out what to do, seeing as there's a large continue button at bottom right of the installer window. If they can't work out what to do, perhaps it is safer for them not to proceed. This is not meant as a criticism of people who may be bewildered by this or any stage of the installer, simply a recognition that a procedure that can wipe out a pre-existing operating system and/or remove a partition containing valuable personal data requires a minimum of technical insight.

---

### Post by Lars Noodén on 2014-07-26
Hmm.  The installer does say that having an Internet connection is a prerequisite and when a wireless network does require a password, the correct keyboard layout is needed.  So I'd say querying for the keyboard ought to come first and thus you have found a bug in Ubiquity.

---

### Post by dandandan on 2014-07-26
@coffeecat 
I disagree, I think you are missing the point.
When people connect who have the password and are unable to enter it due to wrong keymap, that is, for me atleast, an issue.
The reason i have brought that up is that a friend of mine wanted to install ubuntu and got confused by that, calling me and i quote "this linux crap can not even input [, ubuntu sucks" 
She is able to set up windows and enter the password, she should be able to do the same thing with ubuntu.
Its not an issue about not being able to click on "not right now", its an issue of ubuntu wanting text input from the user using the wrong keymap.
Its only logical to set the correct keymap before asking for textinput.

---

### Post by coffeecat on 2014-07-26
> **dandandan said:**
> When people connect who have the password and are unable to enter it due to wrong keymap, that is, for me atleast, an issue.

That's a valid point.

However, when the installer starts you can change the language from the default English, which at least gives you the correct character set, even if not the correct keyboard layout. I have some sympathy with this problem. The installer defaults to the US keyboard layout which has significant differences from the UK layout for a number of non-alphabetical characters. I've got used to this now, but it would be an obstacle for those who don't know where to find the misplaced characters.

Out of interest, which particular combination of language and keyboard layout confounded your friend?

---

### Post by bapoumba on 2014-07-26
Just to note as I have been doing several installs over the past few days. We have azerty keyboards here. If I choose English as the language for the installer, it sets up a qwerty keyboard. If I choose French, it sets up the proper azerty layout. My own workaround was to plug in the ethernet cable during the install in English (I understand it may not be possible for your friend). I think the installer should ask for both language of the interface and keyboard layout at the very first screens.
The install in English I prefer, because switching languages thereafter sometimes messes up the default file names (for ex the Download folder wich has a different name in French). I have a qwerty keyboard layout pic in my phone so that I can work out the manual partition and mount points to my likings during the install process :)

---

### Post by grahammechanical on 2014-07-26
May I add a point or two? Your friend's computer, did it have Windows pre-installed? If people had to install Microsoft Windows would they find it so easy? I do not think so. In the beginning Microsoft only knew of the existence of one keyboard layout and that was USA.

The wireless pass phase is usually an alpha-numeric combination. Is it so hard to work out the correct keys for those few letters? An ethernet connection is preferable anyway. There might not be a driver module for the driver adapter.

Regards.

---

### Post by buzzingrobot on 2014-07-26
> **bapoumba said:**
>  I think the installer should ask for both language of the interface and keyboard layout at the very first screens.

Fedora's installer, Anaconda, does that at the very first screen. Ubuntu should, as well.  Asking for a password to be entered before determining language and keyboard layout is a design bug.

---

### Post by bapoumba on 2014-07-26
I'm searching for existing relevant bugs. If anyone know of them, please post the link.

I should add one more point. After installing in English, only can I set up an azerty keyboard after installing the French language packs. So I'm not sure against which package I should report that.

Edit [https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1284635](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1284635) ?

---

### Post by grahammechanical on 2014-07-26
As anybody thought of loading to the live session desktop and changing the keyboard layout and then running the installer?

---

### Post by Lars Noodén on 2014-07-26
> **bapoumba said:**
> I'm searching for existing relevant bugs. If anyone know of them, please post the link.

I should add one more point. After installing in English, only can I set up an azerty keyboard after installing the French language packs. So I'm not sure against which package I should report that.

Edit [https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1284635](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1284635) ?

#1284635 is with ibus and seems to be after the installation.  In #3 above, the problem is during the installation process so that would be with ubiquity.  I'm not good at finding old bugs in Launchpad but did try a bit and did not find anything.  Perhaps this is a new bug.

---

### Post by bapoumba on 2014-07-26
> **grahammechanical said:**
> As anybody thought of loading to the live session desktop and changing the keyboard layout and then running the installer?
Not here. These are older, lower end machines, and a live environment, be it lubuntu, is really slow. So I went directly to "Install lubuntu".

> **Lars Noodén said:**
> #1284635 is with ibus and seems to be after the installation.  In #3 above, the problem is during the installation process so that would be with ubiquity.  I'm not good at finding old bugs in Launchpad but did try a bit and did not find anything.  Perhaps this is a new bug.

[https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/1297234](https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/1297234) < The live environment does not have all the language packs, I can understand that. Choosing the language during the install did get me the right keyboard layout, which is what it is supposed to do. May be I'm asking for the impossible, ie an English interface with a French keyboard. At least the older text mode installer would allow me to do it.
An interesting thread where I got the idea to search for bugs related to console-setup : [http://ubuntuforums.org/showthread.php?t=2132617](http://ubuntuforums.org/showthread.php?t=2132617)

---

### Post by dandandan on 2014-07-26
@coffeecat

She has a german keyboard, no idea what language she used, i guess default english.

@grahammechanical
She installed Windows herself and had no issues with it. Even if it was hard to install windows, does not mean installing ubuntu should be hard. I, for example, use linux because i find it easier to handle than windows. 
The passphrase is something with ()(+*)(/&% characters, that is indeed hard to figure out, and it requires a user to know that its not simply "not working properly" but a different layout is loaded.  If a user does not know that, he/she will think "i can't even type properly with this linux" and not search for the right positions. Settings layout in live session beforehand works of course.

---

### Post by ian-weisser on 2014-07-27
Seems like a clear usability bug to me. The user's expectation that input will be the same as what is typed is valid.

Grahammechanical has pointed out some excellent workarounds.

---

