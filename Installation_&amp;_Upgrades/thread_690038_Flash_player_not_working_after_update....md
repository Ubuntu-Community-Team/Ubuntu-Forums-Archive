---
title: "Flash player not working after update..."
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by xr600 on 2008-02-07
Just updatet my system with a new version of the flashplayer (autoupdate), and now nothing seems to do work in firefox... Any ideas ?!, can I revert the process somehow ^??!.


Regards.

Torben

---

### Post by zvacet on 2008-02-07
Chek in var/cache/apt/archives do you have two versions of Flash.If you have than(still in that folder)

```
sudo dpkg -i lower version
```

lower version=exact name of your lower version

That should downgrade it.After that go to the synaptic and find flash(see if it is your lower version,just in case)>highlight it>go to the package menu>lock version.

---

### Post by aethra on 2008-02-07
same problem here, but with opera

---

### Post by ossaplad on 2008-02-07
same problem. Try this, it worked for me:

sudo apt-get install flashplugin-nonfree=9.0.48.0.2+really0ubuntu12

---

### Post by dada1958 on 2008-02-07
> **ossaplad said:**
> same problem. Try this, it worked for me:

sudo apt-get install flashplugin-nonfree=9.0.48.0.2+really0ubuntu12
Tnx, degradation worked :)

---

### Post by Starlight on 2008-02-07
I have the same problem... I tried doing what you suggested, but I got this error message :(

md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

---

### Post by Dai777 on 2008-02-07
still having problems with the flash plugin. it works ok in in normal use for movies embeded in a web page but not for for movies in a pop up window. [http://dai-videotutes.blogspot.com/](http://dai-videotutes.blogspot.com/)
most of my flash movies use code from blip.tv and can be viewed in a pop-up window but all I get is a grey box with sound.

any ideas what the solution to this problem is.


Just had a bit of a play and removed the flash player plugin from synaptic. re-installed it from pop-up window when it said install missing plugin. 
the pop-up worked ok but, only that particular pop-up. All other pop-up movies still have grey box no movie just sound.
Also if I return to the page to play movies, all movies have grey box with sound but no picture. So complete failure of plugin installation.

---

### Post by Starlight on 2008-02-07
is it possible to tell the flash installer to forget about md5 checking? I tried installing it a few times, and I got that error each time...

---

### Post by executor on 2008-02-07
> **Starlight said:**
> is it possible to tell the flash installer to forget about md5 checking? I tried installing it a few times, and I got that error each time...

same problem her to when i downgrade it..

---

### Post by dandu on 2008-02-07
I had the same problems with this update and Konqueror, it seems to be a problem with Konqueror not supporting XEmbed. Got some info about this new Flash version in here:
[http://blogs.adobe.com/penguin.swf/2007/12/flash_player_9_update_3_final.html](http://blogs.adobe.com/penguin.swf/2007/12/flash_player_9_update_3_final.html)

As the downgrade to an older 'flashplugin-nonfree' doesn't work (md5 mismatch error) I had to uninstall 'flashplugin-nonfree' and manually install an older flash plugin version. 
I got an archive with older versions from here:
[http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip)
and installed flash version '9r48'. Everything is ok now :)

Hope Adobe ppl will fix this fsck up.

---

### Post by lawina on 2008-02-07
Thanks a lot folks. Downgrade worked for me too.

---

### Post by gobuntu on 2008-02-07
> **ossaplad said:**
> same problem. Try this, it worked for me:

sudo apt-get install flashplugin-nonfree=9.0.48.0.2+really0ubuntu12

Thank you ossaplad,

this fixed both Opera and Firefox.

NOW (any one):

1. Why doesn't the new Flash Player version work?

2. As soon as I downgraded Flash Player as above, the "New Updates" icon pops informing of upgrade available for F.P.

3. Since I always accept all avaiable upgrades, how to avoid the new Flashplayer version (till it works OK), while accepting other updates?

Thanks.:)

---

### Post by acl123 on 2008-02-07
What do you guys mean when you say it doesn't work? Mine works for one flash video, then freezes firefox after that... kind of similar to what usually happened with Ubuntu until a couple of months ago. Grumble grumble.

---

### Post by enquiry on 2008-02-07
The problem is not with the Flash Player binary but there's a md5 mismatch which prevents the upgrade from being installed. I haven't researched the issue further, but I did get the new version of Flash installed by doing a *complete removal* via Synaptic and then installing it again. It is not sufficient to do a normal reinstall of the package.

---

### Post by MightyMe on 2008-02-07
Had the same problem and this worked for me:

Uninstall flashplugin in package manager and then re-install it. I now have
flashplugin-nonfree 9.0.48.0.2+really0ubuntu12.1

---

### Post by tsniemi on 2008-02-07
> **enquiry said:**
> The problem is not with the Flash Player binary but there's a md5 mismatch which prevents the upgrade from being installed. I haven't researched the issue further, but I did get the new version of Flash installed by doing a *complete removal* via Synaptic and then installing it again. It is not sufficient to do a normal reinstall of the package.

Complete Removal -> Install worked for me, thanks!

---

### Post by drogatoo on 2008-02-07
Thanks, completely removing of  flashplugin-nonfree and reinstalling did the work for me to

---

### Post by MightyMag on 2008-02-07
Yep, same problem for me. Total uninstall and reinstall did the trick.
A small HOW TO for newbies:
To remove type:
> sudo aptitude remove --purge flashplugin-nonfree

And to install again:
> sudo aptitude install flashplugin-nonfree

---

### Post by CarpKing on 2008-02-07
> **MightyMag said:**
> Yep, same problem for me. Total uninstall and reinstall did the trick.
A small HOW TO for newbies:
To remove type:


And to install again:

Worked for me.

---

### Post by deadsea on 2008-02-07
Here is the single command line to uninstall and purge it and then reinstall it.  It works for me after doing so with firefox.

```
sudo apt-get purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
```

---

### Post by Dai777 on 2008-02-07
tried all of the above but still flash does not work in a pop-up window.
any ideas on this?

---

### Post by Chappy7777 on 2008-02-07
I thank God for this forum. I went to bed with the "my PC is screwed again" blues, and woke up with them. I had placed a post in here yesterday before the UB population en masse had installed the system updates. I had, as I was online when they 1st came on. I installed them, and could no longer do any flash videos, or even go to pages w/Flash running. Worst was, I could not open my Gmail account. I posted all this and got a couple answers that I could not grasp. No one else was having the problem. That was yesterday.

This am I get up and pour my coffee, come in and boot up. I was, at that point, prepared and dreading, the reinstalling of Ubuntu. It's not that the process is hard, but my setup is Feisty 7.04, and I installed it soon after it came out. IOW, I have been working on what I have here for 10 months or so, and to dump all that because of a Flash/Java (?) problem was distressing.

I logged into these forums, looked on this one, and found this thread. 

I went to Synaptic, uninstalled and the reinstalled Flashplugin. Now I can read my mail and I went to You Tube and Praise God, no probs.

POINT /Short version, the synaptic un/re-install worked. I doubt that would have occurred to me. I am too used to Windows where once you install a program, if it messes things up, good luck!

Thanks folks.  I hope my "NooB's venture in Feisty" story didn't bother anyone.

---

### Post by Chappy7777 on 2008-02-07
> **Dai777 said:**
> tried all of the above but still flash does not work in a pop-up window.
any ideas on this?

Did you try this one, it solved that problem and more for me. See above post.

Open Synaptic. Search on "Flash".  Find the "Flashplugin-nonfree" and mark it for uninstall. removal. Hit "apply". let it uninstall the thing. The do another search on Flash. Find Flashplugin again (it should no longer be installed) and click on "Mark for Reinstallation". Hit apply.
Synaptic will do the rest.

All I can say is that it solved my problems, which if you read my post, were the same as yours, and worse, since somehow Gmail is related to the Flash plugin. Somehow.

---

### Post by frodon on 2008-02-07
> **deadsea said:**
> Here is the single command line to uninstall and purge it and then reinstall it.  It works for me after doing so with firefox.

```
sudo apt-get purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
```Worked for me too, thanks.

---

### Post by Dai777 on 2008-02-07
yes been to synaptic un-installs everything (not just the plugin) with flash then did a re-install but pop-up flash still not working.

when I did  un-install flash and reinstalled it from the pop-up using install missing plugin it worked but for only that particular pop-up window all the other pop-up windows still would not work.

and when I came back the original pop-up stopped working. So the plugin still has problem with embedded javascript in pop-up windows.

[http://dai-videotutes.blogspot.com/](http://dai-videotutes.blogspot.com/)

> sudo apt-get purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
Does not seem to be working on the pop-up windows

---

### Post by coffen on 2008-02-07
> **Dai777 said:**
> yes been to synaptic un-installs everything (not just the plugin) with flash then did a re-install but pop-up flash still not working.

when I did  un-install flash and reinstalled it from the pop-up using install missing plugin it worked but for only that particular pop-up window all the other pop-up windows still would not work.

and when I came back the original pop-up stopped working. So the plugin still has problem with embedded javascript in pop-up windows.

[http://dai-videotutes.blogspot.com/](http://dai-videotutes.blogspot.com/)

You need to restart all your browser sessions for it to work.

Do the removal/reinstall. Then close all browser sessions.
Restart your browser and everything should work.

---

### Post by ubuntu-freak on 2008-02-07
If you still have problems, try
 
**rm $HOME/.mozilla/firefox/pluginreg.dat**
 
Firefox recreates it with the updated plugin info. Check out my [how-to](http://ubuntuforums.org/showthread.php?t=661833) if you have other streaming or multimedia issues.
 
Nathan

---

### Post by drbcladd on 2008-02-07
Okay, the remove and reload did the trick for Firefox 2.X.

```

sudo aptitude remove --purge flashplugin-nonfree && sudo aptitude install flashplugin-nonfree
```

It does not, however, fix the problem for Opera (9.25 Build 687). Mimicking reassuringlyoffensive's suggestion for Mozilla I tried removing ~/.opera/pluginpath.ini

The file was regenerated when I restarted Opera but no joy in getting Flash content to appear. Getting unrepainted squares (though the "Click to activate and use this control" message appears and disappears as appropriate). 

Just wondering if there is something else I should try. I could go back to watching all video content in FF.

---

### Post by dmccor1 on 2008-02-07
I am having the same problem since the update today.  I have tried using:

sudo apt-get purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
Up
When I do Update Manager wants me to do the update to the newest version of flash:

flashplugin-nonfree Version 9.0.48.0.2+really0ubuntu12.1: 

When I run the update I received this error message:

E: flashplugin-nonfree: subprocess post-installation script killed by signal (Interrupt)

Any ideas on how to get everything working again?
:confused:

---

### Post by ubuntu-freak on 2008-02-07
Strange how it's not working for some. Try purging it again and install the one in my [how-to](http://ubuntuforums.org/showthread.php?t=661833). I was thinking about removing it now that flash is "fixed". Might leave it there for now. 
 
Nathan

---

### Post by Dai777 on 2008-02-07
Tried your suggestion on purging flash and removing the mozilla file but no joy still the same.
if you can view my movies in a pop-up let me know because then I will know that it is a fault my end, and maybe something I have not done or overlooked. 
[http://dai-videotutes.blogspot.com/](http://dai-videotutes.blogspot.com/)

other wise there is a problem with the flash plugin. either way it would be good to know where the problem is.

---

### Post by Corvair on 2008-02-07
Same here
I have tried every method mentioned, removing and reinstalling flash flayer and I still cannot open flash clips. 
Here is what I keep getting when I try opening video flashes from Yahoo.

Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. 

I have the upgraded version.....12.2 and it does not work.

---

### Post by nikef on 2008-02-07
Same problem here  :confused:

do i really need gnash installed ?

---

### Post by ubuntu-freak on 2008-02-07
> **nikef said:**
> Same problem here  :confused:

do i really need gnash installed ?

 
Even the one in my thread doesn't work? Works for me and others who needed it when the repo one was broken.
 
Nathan

---

### Post by Rumpanzle on 2008-02-08
This [here]("http://ubuntuforums.org/showthread.php?t=679212") helped me to get my Opera 9.25 with 9.0.48 running again.

---

### Post by Dai777 on 2008-02-09
anyone figured out how to get the flash plugin working yet without downloading the rpm package

---

### Post by ubuntu-freak on 2008-02-09
> **Dai777 said:**
> anyone figured out how to get the flash plugin working yet without downloading the rpm package

 
You must be using Opera? Cos the latest one works in FF.
 
Nathan

---

### Post by engelsen on 2008-02-09
I installed Opera 9.50 Beta, and now the latest flash works fine.

[http://www.opera.com/download/?ver=9.50b](http://www.opera.com/download/?ver=9.50b)

It'a a beta release of Opera, but I've been running it on another PC since it was released without problems. It's feels faster also.

Edit:
I took a copy of the "/.opera" folder before installation in case the beta version messed up.

---

### Post by Chappy7777 on 2008-02-09
> **coffen said:**
> You need to restart all your browser sessions for it to work.

Do the removal/reinstall. Then close all browser sessions.
Restart your browser and everything should work.
==================
When I did the flashplugin-nonfree un/re install using Synaptic, I did it with FFox closed. I always close FFox before doing anything using Synaptic (other than if I am looking to see what version I have, and what's available, again, just to look). 

I'm not sure if I need to do this. Maybe it's a carry-over from Windoze days. It just seems that the less programs running, the less chance of problems. Common sense.

---

### Post by Dai777 on 2008-02-09
no I'm using fifrefox and flash works ok for embedded flash but not for pop-up windows 
[http://dai-videotutes.blogspot.com/](http://dai-videotutes.blogspot.com/)
go here and tell me whether you can view the movies in the pop window
if not then still something wrong with the plugin. And yes tried using synaptic with not running ff and shut everything down. Also had the pop window working but when I return it not working.

so not sure what exactly what the problem is.

---

### Post by prayag on 2008-02-10
If its a 64 bit gutsy. You might want to look at[ this]("http://ubuntuforums.org/showpost.php?p=3328950&postcount=7").

Mine is working after this hack.

Regards,
Prayag

---

### Post by Dai777 on 2008-02-11
nope using 32bit version.

---

### Post by ubuntu-freak on 2008-02-13
See paragraph 7 of "Troubleshooting" in my  [how-to](http://ubuntuforums.org/showthread.php?t=661833).
 
Nathan

---

### Post by Corvair on 2008-02-13
I wish some one would make this simple for me (newby) 

I did this: sudo apt-get purge flashplugin-nonfree 

then I downloaded the adobe installer from Adobe: Install_flash_player_9_linux.tar.gz 2.9MB_adobe.com
 I have the flashplayer-installer
When I click on it the flashplayer opens 
Now what do I do with this????


And I try this:
claude@claude-desktop:~$ sudo gdebi -i 
Usage: gdebi [options] filename
For a graphical version run gdebi-gtk


And I try this:
claude@claude-desktop:~$ sudo dpkg -i filename.deb 
dpkg: error processing filename.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 filename.deb
claude@claude-desktop:~$ 

Am I a desperate case?????

:lolflag:

---

### Post by ubuntu-freak on 2008-02-13
Double clicking didn't work? Also, with the terminal way of installing, move the deb to your home folder and use the EXACT filename with .deb at the end. If it said it didn't exist, then you either didn't move it to your home folder or you got the filename wrong.
 
Hope that helps.
 
Nathan
 
P.S. You didn't do "sudo dpkg -i filename.deb" did you? You're supposed to use the actual name of the file.

---

### Post by offline on 2008-02-13
Confirming that after this...[SIZE="3"]disastrous flash update[/SIZE] neither firefox nor opera could play youtube flash videos.
After uninstalling and reinstalling flash plugin free as mentioned in this thread, firefox plays* youtube videos but not the  above mentioned popup videos.
opera is still dead(can't play any flash).

*update
strangely, it can't seem to play many videos of youtube(coincidence? we will see)

---

### Post by ubuntu-freak on 2008-02-13
> **offline said:**
> Confirming that after this...[SIZE="3"]disastrous flash update[/SIZE] neither firefox nor opera could play youtube flash videos.
After uninstalling and reinstalling flash plugin free as mentioned in this thread, firefox plays youtube videos but not the  above mentioned popup videos.
opera is still dead(can't play any flash).

 
Opera still doesn't work even with my links? Version 9.0.48 should work fine with Opera if you purge 9.0.115. Might be worth using Opera 9.5.
 
Nathan

---

### Post by Corvair on 2008-02-13
I have solved my problem. Flash Player is working again.

[COLOR="Red"]SOLUTION:[COLOR="Black"]
I had loaded Forifox version 3. I took it out and reloaded Firefox 2, restarted my computer and Flash is Playing again.[/COLOR][/COLOR]

---

### Post by ubuntu-freak on 2008-02-13
Glad you got it working. Although, making a symlink might have worked
 
**sudo ln -sf /usr/lib/firefox/plugins /wherever/firefox3is** 
 
Nathan

---

### Post by eac on 2008-02-14
I still can't get flash working! The latest version doesn't seem to work, and when I try removing it and installing the older version I get an md5sum mismatch. Any suggestions?

---

### Post by ubuntu-freak on 2008-02-14
> **eac said:**
> I still can't get flash working! The latest version doesn't seem to work, and when I try removing it and installing the older version I get an md5sum mismatch. Any suggestions?

Are you using Firefox? Try paragraph 7 of troubleshooting in my [how-to](http://ubuntuforums.org/showthread.php?t=661833). You might need to install alsa-oss and instruct FF to use it.
 
I can't believe that stupid flash still has the error. Install the new one and try that alsa fix. 
 
Nathan

---

### Post by eac on 2008-02-14
Still not working. Complete description of situation:

I'm using firefox 2.0.0.12
I looked at /etc/firefox/firefoxrc and the line:
FIREFOX_DSP=”aoss”
is already there (I seem to remember doing that a while back...)

I just tried:

1) close firefox
2) sudo apt-get purge flashplugin-nonfree
3) sudo apt-get install flashplugin-nonfree
4) rm ~/.mozilla/firefox/pluginreg.dat
5) Open up firefox

Flash still doesn't work. I tried going to YouTube, got a message claiming I didn't have a recent version of flash and firefox offered to install it, and that failed.

I also tried following the instructions to use the older version of flash, and it doesn't work either, telling me:
"md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed."

Any other suggestions?

---

### Post by ubuntu-freak on 2008-02-14
Check your /usr/lib/firefox/plugins folder and make sure a flash plugin is installed. Maybe reinstalling or purging FF would help. To reinstall use Synaptic or;
 
**sudo apt-get --reinstall install firefox**
 
Nathan

---

