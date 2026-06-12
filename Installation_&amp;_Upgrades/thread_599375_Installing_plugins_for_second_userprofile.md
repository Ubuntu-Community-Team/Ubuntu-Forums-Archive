---
title: "Installing plugins for second user/profile"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by muhkayoh on 2007-11-01
Hello,

I've spent about 30 minutes searching on this with no luck (maybe I just haven't come up with the right search term combo), so I'd appreciate any help.

I recently upgraded to Gutsy with no problems.  (In fact, all of my upgrades have been trouble free going all the way back to Dapper, for what that's worth).  My computer has two users, me and my girlfriend.  I'm also the administrator (i.e., the sudo guy).  Anyway, when I upgraded to Gutsy, my Firefox lost its Flash plugin.  It was no problem, however, because the first time I surfed to a page with flash content, I got a missing plug-in message, clicked and installed the plug-in with no trouble.

My girlfriend, though, is not so lucky.  When she clicks to install the missing plug-in, it fails.  I'm guessing it's a permissions problem (since she isn't the root user), but that seems like a failing as well since she ought to be able to install the plug-ins she needs for her browser in her profile (or at least, that's the way I think it should work).

So, a two-pronged question:

1.  Can I set it up so that she can install her own browser plug-ins without needing me to do something, and if so, how?

2.  Failing that, how do I install the Flash plug-in for her?

Thanks,

Matt

---

### Post by ruggersway on 2007-11-01
> 1. Can I set it up so that she can install her own browser plug-ins without needing me to do something, and if so, how?

You can add her to the sudoers group, depending on how well you trust her to not screw things up...;)

> 2. Failing that, how do I install the Flash plug-in for her?

I'm guessing, but it sounds like the way you installed flash may have installed it into your profile.  I believe if you use apt to install 

**if you don't mind non-free solutions... 
$ sudo apt-get install flashplugin-nonfree

or
$ sudo apt-get install mozilla-plugin-gnash

then it will install it globally and should eliminate your problems.

In the past, I've used /etc/skel to put links to plugins for additional users.  But since this is a new distro I doubt you would need to do anything like that.  

Hope this helped

---

### Post by muhkayoh on 2007-11-01
Thanks for the reply.  I'm going to hold off giving her sudo powers.  She already has too many powers in other areas... :D

I did install flash originally the way you suggest, but that was when I had a previous verion of Ubuntu.  At any rate, trying to install it now just results in a message saying it's already installed with the latest version.  But your comment about my possibly having installed it to my profile really gets at what I'm wondering here: shouldn't she be able to install it to her profile without involvng sudo powers?  That's how it seems to me that it should work, but for some reason, it doesn't.

Matt

---

### Post by ruggersway on 2007-11-02
Well, I guess you could try (if you haven't already) completely removing the flash plugin and reinstalling it.  I suppose it is possible some of the permissions didn't carry properly from the upgrade.  This is what my plugins for flash look like

User@ares:/usr/lib/mozilla/plugins$ ls -l
total 0
lrwxrwxrwx 1 root root 37 2007-10-18 15:48 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
.
.
Which is just a link to /usr/lib/flashplugin-nonfree/libflashplayer.so

User@ares:/usr/lib/flashplugin-nonfree$ ls -l |grep flash
-rw-r--r-- 1 root root 7040036 2007-10-18 15:48 libflashplayer.so


The flash plugin should be
File name: libflashplayer.so
Shockwave Flash 9.0 r48

You can verify this in firefox, just open a new tab and enter the address about:plugins to see all your installed plugins.


Lastly, under your profile you should have a file ~/.mozilla/pluginreg.dat

-rwx------ 1 user user 2112 2007-10-25 14:44 pluginreg.dat

Compare that to the pluginreg.dat under her profile, you should see an entry for the flash plugin in both.  If you do then I'd look at permissions on the plugins, if for some reason the entry does not exist in her profile you can copy your pluginreg.dat to her profile.  Just make sure the correct user/group permissions exist after the copy so she can read it.

Let me know if this doesn't allow you to resolve the issue.

---

### Post by muhkayoh on 2007-11-02
Thanks again.

I have in fact done the reinstall and that doesn't resolve the issue.  I'll look at some of the other ideas you mention, but let me restate what seems to be the underlying problem to me, because it's that that I'd like to resolve - as opposed to merely getting flash to work under her profile.

I first started using Ubuntu during Dapper.  I subsequently upgraded to Edgy and it was during this time that I added my girlfriend's profile.  At that time, both users had working flash plugins for firefox (although, if I remember, that was before the flash 9 for linux came out, so it worked but not well).

Then I later upgraded to Feisty and - as a result - both users lost the flash plugin.  In my case, it was easily resolved.  The first time I landed on a page with flash content, I was prompted by the browser to install the flash plugin, I did so, and it worked.  Not so for my girlfriend; her install always failed.  I eventually - after some surfing and questioning - got it working on her side and then forgot about it.

Now fast-forward to my recent Gutsy upgrade. The same thing happened: both users lost the plugin after the upgrade, mine was an easy fix and hers isn't.

It seems to me that a user **should** be able to install and uninstall firefox browser plugins independently and it's really **that** problem that I'd like to fix if possible (as opposed to simply finding some administrative route to get it installed for her).  So is that possible?  Or do things not work that way under Ubuntu?

And, to be clear, I do appreciate the help you're offering and will use some such method to get flash working for her if it comes to that.  I'd just really like to get this underlying issue resolved if at all possible.

Thanks again,

Matt

---

### Post by ruggersway on 2007-11-02
I am not aware of a way to individually install the plugin per profile, other than downloading directly from adobe and following their instructions.  The only time I'd done that was on Fedora 5, never had a need to on Ubuntu.

That being said, the same theory may apply - this is likely the end of my advice on this.  You can go to Adobe and download the tar.gz for flash, unpack it and copy the plugin to ~/.mozilla/plugins directory.

**I've not tried this in Ubuntu.  It seemed to me that Ubuntu was trying to eliminate the need for this type of installation.  

I understand your desire to enable the user to install the plugin themselves, I wish I had an easier answer for that.  But the way I understand the setup in Ubuntu, the places the user would need to install the plugins are protected directories rather than in each profile.  This eliminates the need for each user to have to install each plugin.

I wish I could be more help.  If ~/.mozilla/plugins does not satisfy what you are looking for then I am afraid I can't be much more help.

--you don't have to give full-blown sudo rights.  You can limit what she can do.

Hopefully someone else can better help you.
.
.

---

### Post by muhkayoh on 2007-11-28
I'm reviving this because I never have been able to solve the problem and it's really frustrating.  The .mozilla/plugins directory is owned by my girlfriend (since it's in her profile).  I can't view the directory to verify the contents, nor can I copy or figure out any other way to get the flash plugin installed there.  She's continually prompted by flash-containing web pages to install the plugin, she follows the steps, and is always rewarded with failure.  Surely there must be some way to get flash working under her profile?

Thanks for any help.

Matt

---

