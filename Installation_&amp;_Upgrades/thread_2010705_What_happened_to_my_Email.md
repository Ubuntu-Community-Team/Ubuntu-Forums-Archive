---
title: "What happened to my Email?"
date: 2012-06-25
forum: Installation &amp; Upgrades
---

### Post by hbnmgr on 2012-06-25
After recent upgrade Thunderbird comes up with NO ACCOUNT.

Funny - I have all favorites in Mozilla.

What happened in the upgrade the destroyed my Email Account?

Had I known that, I would have made backups!

Any suggestions .. is it hidden somewhere?
Or do simply chalk it up to incompetent programmers and set my account back up?
Moreover, I don't like the desktop. Can't get used to all the changes. What other screwed up changes to we have to look forward to?  How many mishaps, mistakes, disappearing acts should we expect from you brainiacs.  Keep it up if want to ruin what was a good thing.

hbnmgr

---

### Post by black veils on 2012-06-26
> I don't like the desktop. Can't get used to all the changes. there is no need to get used to the new desktop, you could either install a limited version of what you had before, onto the current system ```
sudo apt-get install gnome-panel
```or, what i would recommend, for plenty of customisation options, is to install another desktop called xfce, this can be done by ```
sudo apt-get install xubuntu-desktop
```you can choose how many panels, the sizes, transparency, plug-ins, panel background image, window decorations, and other general settings.

---

### Post by haqking on 2012-06-26
> **hbnmgr said:**
> A

**Had I known that, I would have made backups!**



Backups are proactive, not reactive.

---

### Post by hbnmgr on 2012-07-01
> **black veils said:**
> there is no need to get used to the new desktop, you could either install a limited version of what you had before, onto the current system ```
sudo apt-get install gnome-panel
```or, what i would recommend, for plenty of customisation options, is to install another desktop called xfce, this can be done by ```
sudo apt-get install xubuntu-desktop
```you can choose how many panels, the sizes, transparency, plug-ins, panel background image, window decorations, and other general settings.


So Apparently the programmers did decided to NOT Keep Email Accounts and Settings during an Upgrade!!!  Correct?  And apparently there is nothing we can do about, and nothing you are going to do about it ! Correct?!?!?

So what is the command to install Ubuntu Studio which is what I had prior to the Update? Else, if not possible, How can I roll back to the previous and will my Email account be there?

ATTN: Forum Trolls - While I am MAD as Hellfire, I'm trying to be as polite as possible under the circumstances you people put me in by relying on your programming and so called updates!!!

---

### Post by darkod on 2012-07-01
Have you looked into your Home folder, in the hidden folders?

Not sure if thunderbird is inside mozilla or a separate folder, but it keeps the profile folder with all the data and settings. Unless you changed the default location of the profile.

And when you say "Ubuntu Studio which is what I had", you mean you now have only a different interface or a different distribution? Things can go wrong during upgrades but I still haven't seen to upgrade you into a different distribution.

You should still have Studio, regardless what you think about the interface.

---

### Post by haqking on 2012-07-01
> **hbnmgr said:**
> **So Apparently the programmers did decided to NOT Keep Email Accounts and Settings during an Upgrade**!!!  Correct?  And apparently there is nothing we can do about, and nothing you are going to do about it ! Correct?!?!?

So what is the command to install Ubuntu Studio which is what I had prior to the Update? Else, if not possible, How can I roll back to the previous and will my Email account be there?

ATTN: Forum Trolls - While I am MAD as Hellfire, I'm trying to be as polite as possible under the circumstances you people put me in by relying on your programming and so called updates!!!

This is a public forum, you seem to be talking to the programmers who are rarely here, you are talking to the world.

Also as for incompetence, besides being rude, it would fall on your shoulders, as no one forces an upgrade, and you should have back ups.

And no one but you put yourself in your position.

Peace

---

### Post by hbnmgr on 2012-07-01
Darkod Wrote:

> Have you looked into your Home folder, in the hidden folders?

Not sure if thunderbird is inside mozilla or a separate folder, but it  keeps the profile folder with all the data and settings. Unless you  changed the default location of the profile.

And when you say "Ubuntu Studio which is what I had", you mean you now  have only a different interface or a different distribution? Things can  go wrong during upgrades but I still haven't seen to upgrade you into a  different distribution.

You should still have Studio, regardless what you think about the interface.

Looked in Home Folder - Nada

What is hidden Folders ???

ThunderBird is separate folder - Only thing in there is JS file.

I did not change Default location or anything else - Simply Updated and it did what it was programmed to do.

It seems I have a different interface, with a row of icons on the left side for ...
Home Folder
Web Browser
Libre Office writer, calc, impress
Ubuntu Software Center
Ubuntu One
System Settings
Workspace

Don't know what the default is, and don't know what desktop interface this is.
How can I find out, and is there one for Ubuntu Studio? Or does XFCE and Gnome interfaces designed to work with the various Ubuntu Operating Systems?

Still can't find all my Emails. Did the programmers forget this logical step? Are they listening? Did I loose all my Emails? During an Upgrade, is all info destroyed? All Folders? Can backup to a Folder or will it be destroyed?

Come on people ... We need to know what to do before the next upgrade? If this is not the right forum ... please direct me where to post in order to ask the right people. Otherwise we are all wasting our time. Time is money ! ! !  And I'm running out.

---

### Post by darkod on 2012-07-01
When you open your Home folder, press Ctrl + H and it will show the hidden folders. They start with a dot in their name.

I definitely know there is .mozilla folder but not sure if the thunderbird profile is stored there. Take a look.

The interface you are describing is the Unity interface coming with the Desktop version since 11.10.

I am not sure which interface Studio uses since I have never used it.

---

### Post by darkod on 2012-07-01
I just checked, when you press Ctrl+H there should be .thunderbird folder. When you open it, the default profile folder ends with .Default.

In there should be the mailbox (all mails).

---

### Post by hbnmgr on 2012-07-06
> **darkod said:**
> I just checked, when you press Ctrl+H there should be .thunderbird folder. When you open it, the default profile folder ends with .Default.
 
In there should be the mailbox (all mails).
 
 
OK - I found a .thuderbird Folder in Hidden folders, found .default and crash reports folder and profiles.ini in there. But ThunderBird is obviously not reading it. Why Not? and How do I make it do so???
 
Thanks!

---

### Post by darkod on 2012-07-06
I have no idea why it's not reading it. You can check in profiles.ini whether the path is correct, but I have the feeling it will be.

In theory, all the info is inside that profile folder. So, you can create a new profile, no need to start entering data or anything. Then simply copy the content of the blahblah.default folder into the newly created one.
When you open Thunderbird it should open the new profile (default) but it will have your data inside.

---

### Post by hbnmgr on 2012-07-06
[https://wiki.ubuntu.com/UbuntuStudio/11.10release_notes](https://wiki.ubuntu.com/UbuntuStudio/11.10release_notes)
 
Apparently, and according to the above mentioned page (release notes), the programmers are "transitioning to XFCE" and v11.10 suffered an "almost COMPLETE TEAM FAIL during this cycle". This could explain all the problems I've been having.

I will roll back to previous version and wait till the next LTS upgrade is available.

Thanks - and I hope I don't get punished for this post also.

---

### Post by hbnmgr on 2012-07-06
What do you know ... It shows 12.04 is ready.  Will upgrade and see if this one works, and will post results.

---

### Post by darkod on 2012-07-07
Actually 12.04 LTS has been out since April. But since you were running 11.04 it shows option to upgrade only to the next version, 11.10.

Only the LTS versions offer upgrade from one LTS to the next one without all the versions in between.

I would recommend you seriously consider making a clean install of 12.04 LTS, not upgrade from 11.10. And to make it with separate /home partition.

That way all your data inside /home is kept on a separate partition and you can use it even if you make a clean install formatting root. You simply use the /home partition with mount point /home and without formatting, and all your data is there. That will also include all the settings kept inside /home.

If you prefer doing upgrades, not clean installs, you have to accept that they do go wrong sometimes. You can also choose to use only the LTS versions and not upgrade to each version at it comes out. Upgrading every 6 months only enlarges the possibility things to go wrong.

---

