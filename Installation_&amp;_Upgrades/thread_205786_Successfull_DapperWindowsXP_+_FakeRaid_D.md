---
title: "Successfull: Dapper/WindowsXP + FakeRaid :D"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by PandorsBox on 2006-06-29
I haven't played with linux in quite a few years (I primarilly use a computer to play video games, so Windows was (and still is) the best choice), but *something* about Ubuntu made me want to go ahead and give Linux another chance.

So I ordered and recieved some new SATA hard drives (4x Hitachi Deskstars), gave away my PATA drives to some needful friends, splistreamed a copy of XP with the VIA SATA drivers, and started researching my install strategy for Ubuntu.

Of course, I liked what I saw here: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

And so I began my slightkypainfulbutmaybeinagoodway journey, but I made it through just fine in the end.  I can say right now, I'm a happy installer.

A few things I made note of that may help others:

1) The author in that Howto refers to the Ubuntu "LiveCD"...  I can only assume that since that Howto has been released/modified, Ubuntu has changed the name to "Desktop CD".  Threw me for a loop for a bit... but I eventually figured it out.

2) I believe I figured out what that dmraid installation is (the one referred to in the wiki as: "install of dmraid failed (--configure), indicating it was unable to start the dmraid initscript").  Well, for hours I was trying to get past this error... I figured, 'Just my luck, right?'  Well... I checked my /proc directory... it was empty, and it was not supposed to be.  One of the previous mounts must have failed or I didn't type something right... Well, I exited out of chroot, and retyped *all* of the mount commands in the wiki just to be sure.  After that, it worked like a charm.

3) The other thing that confuzzled was the absence of what to do in place of the "base-config new" command -- since that doesn't exist in Dapper.  Well...  I searched the forums, and no one came up with anything new, so I just kept on trucking, expecting my installation to fall on its face.  

It didn't... the only thing that I've noticed so far that went wrong was that there was no "initial user" created since I bypassed the normal install process.  Well, I was still able to get to a shell through the maintenance bootup opton in Grub and use the adduser command to make a new user and password.  Then I noticed that I wasn't in the sudoers list, so I added that too using the visudo command.

So far, so good.  Works like a charm... Of course it's very vanilla looking, but I'll fix that!  Hope this helps someone.

---

