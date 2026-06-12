---
title: "How to get flash working under Lucid?"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by odinb on 2010-04-30
Hi!

Have done a fresh install of Lucid on 2 machines (64-bit), and cannot get flash to work. One machine is AMD/ATI based, the other one Intel/Nvidia, so I do not think it is HW related.

Have installed Medibuntu, Ubuntu restricted extra, and flashplugin-nonfree. Icedtea/OpenJDK is running on the Intel machine, and Sun Java on the AMD, but I do not think java matters.

Going to [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/) and clicking "Test your Adobe Flash Player installation", it tells me I have version 10,0,45,2 installed, and I do see the animated/spinning flash logo, and "successfully installed" when the page loads.

So far so good! So then my daughter wants to play one of her favorite games on PBSkids, and then it is a no-go!

Going to [http://pbskids.org/curiousgeorge/games/pogo_gogo/pogo_gogo.html](http://pbskids.org/curiousgeorge/games/pogo_gogo/pogo_gogo.html) and waiting for the green play button to appear, and clicking it, nothing happens!

It does change between 2 shades of green when mouse-over, but the game never starts, even if I click several times, and wait patiently in-between.

This game works perfectly on my other Karmic 64-bit install.

Any ideas? Have googled around a bit, and cannot find anything helping out here.

---

### Post by itang sanjana on 2010-04-30
Sometimes Icedtea/OpenJDK could be the problem. IMHO Which machine was working?

---

### Post by phillw on 2010-04-30
Hi, I'd suggest removing icedtea, it *may* be clashing with flash.

[http://lovinglinux.megabyet.net/?page_id=220#Flash-videos-display-only-a-symbol-and-won%27t-start-2](http://lovinglinux.megabyet.net/?page_id=220#Flash-videos-display-only-a-symbol-and-won%27t-start-2)

Has some help on flash, from lovinglinux. His support thread on the forum is at [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

Regards,

Phill.

---

### Post by odinb on 2010-04-30
> **itang sanjana said:**
> Sometimes Icedtea/OpenJDK could be the problem. IMHO Which machine was working?

All of them with Karmic, but none with Lucid. 64-bit was used for both Karmic and Lucid.

Tried removing Icedtea/OpenJDK and installing Sun Java on one of the Lucid machines, but no difference.

> **phillw said:**
> Hi, I'd suggest removing icedtea, it *may* be clashing with flash.

[http://lovinglinux.megabyet.net/?page_id=220#Flash-videos-display-only-a-symbol-and-won%27t-start-2](http://lovinglinux.megabyet.net/?page_id=220#Flash-videos-display-only-a-symbol-and-won%27t-start-2)

Has some help on flash, from lovinglinux. His support thread on the forum is at [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

Regards,

Phill.

As said before, have tried removing Icedtea/OpenJDK on one machine, but still no go.

Will try lovinglinux guide on "Flash Optimization - Removing Conflicting Plugins" and see if that helps.

Thanks!

---

### Post by EllyBilateralCI on 2010-04-30
> **odinb said:**
> Hi!

Have done a fresh install of Lucid on 2 machines (64-bit), and cannot get flash to work. One machine is AMD/ATI based, the other one Intel/Nvidia, so I do not think it is HW related.

Have installed Medibuntu, Ubuntu restricted extra, and flashplugin-nonfree. Icedtea/OpenJDK is running on the Intel machine, and Sun Java on the AMD, but I do not think java matters.

Going to [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/) and clicking "Test your Adobe Flash Player installation", it tells me I have version 10,0,45,2 installed, and I do see the animated/spinning flash logo, and "successfully installed" when the page loads.

So far so good! So then my daughter wants to play one of her favorite games on PBSkids, and then it is a no-go!

Going to [http://pbskids.org/curiousgeorge/games/pogo_gogo/pogo_gogo.html](http://pbskids.org/curiousgeorge/games/pogo_gogo/pogo_gogo.html) and waiting for the green play button to appear, and clicking it, nothing happens!

It does change between 2 shades of green when mouse-over, but the game never starts, even if I click several times, and wait patiently in-between.

This game works perfectly on my other Karmic 64-bit install.

Any ideas? Have googled around a bit, and cannot find anything helping out here.

Try this:

sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer

---

### Post by odinb on 2010-04-30
> **EllyBilateralCI said:**
> Try this:

sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer

Failing, since I sit behind a proxy, and the script insists on using port 80....

"Connecting to download.macromedia.com|96.7.67.191|:80... failed: Connection timed out."

Will try again when I get home...

---

### Post by odinb on 2010-04-30
> **odinb said:**
> Will try again when I get home...

Worked like a charm on both machines! :P

So I guess it does not matter if you run Icedtea/OpenJDK or Sun Java.

Thanks from me as well as my daughter! She can now play her flashgames again!

She was not happy about the Lucid upgrade, since it broke her games. Hopefully it is forgotten now.

---

### Post by EllyBilateralCI on 2010-05-01
> **odinb said:**
> Worked like a charm on both machines! :P

So I guess it does not matter if you run Icedtea/OpenJDK or Sun Java.

Thanks from me as well as my daughter! She can now play her flashgames again!

She was not happy about the Lucid upgrade, since it broke her games. Hopefully it is forgotten now.

Yay! \\:D/

I'm really pleased it worked guess I've not lost my former software tester/programming skills as I'm a full time mum!

---

### Post by ds3 on 2010-05-02
I am also unable to get Flash to work on my 64 Bit (AMD) system since updating to Lucid yesterday. I have tried both the Adobe PPA listed above and manual installation. In both cases Adobe's page tells me I have 10,0,45,2 installed, as does about:plugins, but nothing works, including Adobe's animation. I don't have any of the typical conflicting (Gnash, etc.) add ins installed and everything worked fine before switching to Lucid. I'm not sure if this is something with Lucid, or something with Firefox 3.6.3, since that updated along with Ubuntu.

I really have no idea on this, and would welcome any suggestions.

Thanks.

---

### Post by ds3 on 2010-05-02
That was supposed to read about:plugins without the smiley that got automatically inserted...

---

### Post by EllyBilateralCI on 2010-05-02
> **ds3 said:**
> I am also unable to get Flash to work on my 64 Bit (AMD) system since updating to Lucid yesterday. I have tried both the Adobe PPA listed above and manual installation. In both cases Adobe's page tells me I have 10,0,45,2 installed, as does about:plugins, but nothing works, including Adobe's animation. I don't have any of the typical conflicting (Gnash, etc.) add ins installed and everything worked fine before switching to Lucid. I'm not sure if this is something with Lucid, or something with Firefox 3.6.3, since that updated along with Ubuntu.

I really have no idea on this, and would welcome any suggestions.

Thanks.

Can you open a Terminal (Applications -> Accessories -> Terminal) and type in:

sudo update-flashplugin

Please let me know what it says.

---

### Post by ds3 on 2010-05-02
sudo update-flashplugin results in:

sudo: update-flashplugin: command not found

I don't think update-flashplugin works with the 64 bit repository from Adobe, but I'd still welcome any suggestions.

Thanks.

---

### Post by ds3 on 2010-05-02
So it appears a few things do work, but most don't.
Some YouTube videos do play, but not all of them. They're definitely using Flash because right-clicking brings up the Flash menu.
However, pretty much nothing else recognizes Flash and sites tell me to install it.
I do not have Gnash, nspluginwrapper, or any other versions I can locate installed. It is just the 64 bit plugin.
Icedtea is not installed.
This worked fine before the move to Lucid, but I can't tell if it's that or Firefox 3.6.3 that's having the issue.

---

### Post by Kereltis on 2010-05-02
> **odinb said:**
> Hi!

Have done a fresh install of Lucid on 2 machines (64-bit), and cannot get flash to work. One machine is AMD/ATI based, the other one Intel/Nvidia, so I do not think it is HW related.

Have installed Medibuntu, Ubuntu restricted extra, and flashplugin-nonfree. Icedtea/OpenJDK is running on the Intel machine, and Sun Java on the AMD, but I do not think java matters.

Going to [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/) and clicking "Test your Adobe Flash Player installation", it tells me I have version 10,0,45,2 installed, and I do see the animated/spinning flash logo, and "successfully installed" when the page loads.

So far so good! So then my daughter wants to play one of her favorite games on PBSkids, and then it is a no-go!


Going to [http://pbskids.org/curiousgeorge/games/pogo_gogo/pogo_gogo.html](http://pbskids.org/curiousgeorge/games/pogo_gogo/pogo_gogo.html) and waiting for the green play button to appear, and clicking it, nothing happens!

It does change between 2 shades of green when mouse-over, but the game never starts, even if I click several times, and wait patiently in-between.

This game works perfectly on my other Karmic 64-bit install.

Any ideas? Have googled around a bit, and cannot find anything helping out here.

I have the same problem, I've tested FLASH on the website and it say "You have version 10,0,45,2 installed" but some youtube and BBC videos don't work. I can see the video but the controls don't respond, play...etc. I'm using Lucid 64bit and have 64bit flash installed. Most videos seem to work, it's strange. I've tried a few fixes but none of them seem to work. I installed VLC player yesterday and I am wondering if that has something to do with it.

Update: Ok, it appears the videos don't work when embedded on other  sites. If I right click on them and choose 'Watch on Youtube' they work.  The controls still don't work for them though, I can't pause them.

---

### Post by ds3 on 2010-05-02
Okay, so maybe this is related and maybe it isn't, but I'm also having problems with the Java plugin.
In this case, Sun's website and about:plugins recognize the plugin, but Java based sites don't seem to be working.
I only have Sun's version 6 update 20 of Java installed, along with the Firefox plugin. I don't have any of the Ubuntu versions of Java or 32 bit versions installed.
I used the canonical parter repository for the installation.

Thanks in advance for any help.

---

### Post by ds3 on 2010-05-02
Okay, so my problem in both cases was the Ghostery add-in, which I disabled.
I now have everything working and will go post a bug at Ghostery.

Thanks.

---

### Post by jimmyjazz951 on 2010-05-02
I've had the same problem as mentioned here.  I do not have Ghostery installed but took a chance and disabled Adblock Plus.  Flashed worked perfectly.

---

### Post by jalexstark on 2010-05-03
If you read or post to this thread you should be sure to understand that Lucid is broken behind a web proxy.  The Network-proxy -> Apply-system-wide procedure does not work.  apt-get can be fixed by separately going into the preferences and setting the proxy there, but that causes a real problem with, for instance,

flashplugin-installer
ttf-mscorefonts-installer

because the proxy is not fixed for all http access.  Packages such as these download by a delegate of apt-get, not by apt-get (or Synaptic) itself, so they do not know about the proxy.

I had the luxury of a non-proxy network to hand.

If someone knows of a general fix, please post a link.

---

### Post by Kereltis on 2010-05-03
I just installed the pre-release updates and everything appears to be working fine now. :)

Nope, youtube is working fine but I can't play Flash embedded on other sites.

---

### Post by Scibax on 2010-05-04
The problem is not flash player at all.  Ubuntu enables desktop effects by default and it seems to have an issue in this iteration.  To solve your issue with flash controls, disable all the desktop effects.  I think they should disabled by default anyway since it's just bloat and more lines of code to introduce bugs in.  

Right click on desktop, click "Change Desktop Background", click "Visual Effects", and click "None".  Many of your problems will be solved by disabling this Windows style feature.  This feature also can cause graphic glitches in many games as well.

---

### Post by odinb on 2010-05-04
> **Scibax said:**
> The problem is not flash player at all.  Ubuntu enables desktop effects by default and it seems to have an issue in this iteration.

Are you sure? Because i am not! I run full desktop effects, and flash on 64-bit Lucid works just fine for me after using the suggested PPA in post 5 in this thread.

---

### Post by Kereltis on 2010-05-04
> **odinb said:**
> Are you sure? Because i am not! I run full desktop effects, and flash on 64-bit Lucid works just fine for me after using the suggested PPA in post 5 in this thread.

I just copy & pasted this into terminal:

**sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get  update && sudo apt-get install flashplugin64-installer**

As described in post 5 and it worked, everything back to normal, plus I have effects on full!
Thanks Guys! :D

---

### Post by reiki on 2010-05-04
way too complicated, folks.... on a fresh Lucid install, first thing I did was go to the Ubuntu Software Center and install Ubuntu Restricted Extras. Done deal. Flash works fine. Even that pogo pogo thing in the OP first post.

---

### Post by Scibax on 2010-05-04
The flashplugin64 worked very slowly on this machine.  The regular Ubuntu flash plugin works fine when the visual effects are disabled.  If I enable the visual effects, flash still works but the playback controls in Youtube no longer function.  Something is not clicking with the visual effects and flash plugin.

---

### Post by lavinog on 2010-05-04
> **reiki said:**
> way too complicated, folks.... on a fresh Lucid install, first thing I did was go to the Ubuntu Software Center and install Ubuntu Restricted Extras. Done deal. Flash works fine. Even that pogo pogo thing in the OP first post.

The restricted extras doesn't install the 64bit flash on 64bit machines...This is because the 64bit flash is an alpha version.

---

### Post by cybrsaylr on 2010-05-04
> **lavinog said:**
> The restricted extras doesn't install the 64bit flash on 64bit machines...This is because the 64bit flash is an alpha version.

Glad you pointed out the Ubuntu Software Center and installing Ubuntu Restricted Extras is for 32 bit Lucid versions.

I also have the 64 bit version of Lucid and got the code off this forum but can't find the thread. That thread listed 3 lines of code to put in Terminal. I did that and Flash works fine.

---

### Post by naaman on 2010-05-06
> **jalexstark said:**
> If you read or post to this thread you should be sure to understand that Lucid is broken behind a web proxy.  The Network-proxy -> Apply-system-wide procedure does not work.  apt-get can be fixed by separately going into the preferences and setting the proxy there, but that causes a real problem with, for instance,

flashplugin-installer
ttf-mscorefonts-installer

because the proxy is not fixed for all http access.  Packages such as these download by a delegate of apt-get, not by apt-get (or Synaptic) itself, so they do not know about the proxy.

I had the luxury of a non-proxy network to hand.

If someone knows of a general fix, please post a link.

I had to edit /etc/wgetrc with the following lines:

```
# You can set the default proxies for Wget to use for http, https, and ftp.
# They will override the value in the environment.
https_proxy = http://user:pass@proxy.company.com:8080/
http_proxy = http://user:pass@proxy.company.com:8080/
ftp_proxy = http://user:pass@proxy.company.com:8080/

# If you do not want to use proxy at all, set this to off.
use_proxy = on
```

It seems that when dpkg spawns a wget, it must not use the root/current user proxy settings and requires it to be set in /etc/wgetrc..

HTH

---

### Post by odinb on 2010-05-07
> **naaman said:**
> I had to edit /etc/wgetrc 

Thanks, good to know for next time!

---

### Post by NarfZilla on 2010-05-12
Hi!

This solution (sevenmachines app) totally worked for me... until I shut down the computer. :(

Now every time I'm on Ubuntu it just stops working, and I have to remove it and install it again!

Does somebody is having the same issue? How can I fix it?

thank you very much!

---

### Post by EllyBilateralCI on 2010-05-12
> **NarfZilla said:**
> Hi!

This solution (sevenmachines app) totally worked for me... until I shut down the computer. :(

Now every time I'm on Ubuntu it just stops working, and I have to remove it and install it again!

Does somebody is having the same issue? How can I fix it?

thank you very much!

Have you checked [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) to see if it is still working?

Do you have Ubuntu Update Manager to update software automatically or do you have it to notify you first?  

What is it that you're trying to use that has stopped functioning?

---

### Post by NarfZilla on 2010-05-12
Version Information: You have version 10,0,45,2 installed


Actually, it stops working after a while...

The Ubuntu Update Manager asks before install anything.

I did like your other post says:
```

sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer
```

but after some time using the pc, it doesn't work anymore, and I have to remove it, and install it again.

thanks

---

### Post by EllyBilateralCI on 2010-05-12
> **NarfZilla said:**
> Version Information: You have version 10,0,45,2 installed


Actually, it stops working after a while...

The Ubuntu Update Manager asks before install anything.

I did like your other post says:
```

sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer
```but after some time using the pc, it doesn't work anymore, and I have to remove it, and install it again.

thanks

Hi, thanks for posting back.  

Can you tell what program you were playing/using with so that I can replicate your problem, if I can.  I'm trying to find a solution for you and the only way is to tell me what program that is no longer using the flash.

You see when I used the adobe flash test that I mentioned earlier - it is displaying the flash logo and saying it is successfully installed.   So that is why I mentioned the adobe flash test to you to see if you can see it saying "successfully installed".

---

### Post by NarfZilla on 2010-05-12
I am on Firefox 3.6.3 on Ubuntu Lucid Lynx 64.

For a while it says that the plugin is successfully installed...
some time latter, when it stops working, the flash logo doesn't show anymore.

Thanks

---

### Post by EllyBilateralCI on 2010-05-12
> **NarfZilla said:**
> I am on Firefox 3.6.3 on Ubuntu Lucid Lynx 64.

For a while it says that the plugin is successfully installed...
some time latter, when it stops working, the flash logo doesn't show anymore.

Thanks

Hmmm bizarre because it's the same what I have except my flash is working.  My cogs are thinking away and I wonder if you could go to Applications -> Ubuntu Software Centre and make sure you're at top level e.g. "Get all software" and then type in "flash" in the search box.  I want you to tell me if the following says "Installed" or a green tick under the software name:


[LIST]
[*]Adobe Flash plug-in
[*]Adobe Flash plugin 10
[*]Adobe flash player plugin 64 bilt alpha installer
[/LIST]

---

### Post by lavinog on 2010-05-12
Never mind, I didn't read the package correctly.

---

### Post by NarfZilla on 2010-05-12
ok, here it is:

[LIST]
[*]Adobe Flash Plug-in: Not installed
[*]Adobe Flash Plug-in 10: Not installed (not available for installation... because its 64)
[*]Adobe flash player plugin 64 bit alpha installer: Check!
[/LIST]

I just turn on my computer, and, as I would expect, the flash isn't working... I Will try to install the Adobe Flash Plug-in, and see what happens...

other flash related installed packages:

[LIST]
[*]Ubuntu restricted extras
[*]libswfdec-0.8-0 (SWF (Macromedia Flash) decoder library)
[*]libming1 (Library to generate SWF (Flash) Files)
[*]Commonly used restricted packages for Ubuntu
[/LIST]

---

### Post by EllyBilateralCI on 2010-05-12
> **NarfZilla said:**
> ok, here it is:

[LIST]
[*]Adobe Flash Plug-in: Not installed
[*]Adobe Flash Plug-in 10: Not installed (not available for installation... because its 64)
[*]Adobe flash player plugin 64 bit alpha installer: Check!
[/LIST]

I just turn on my computer, and, as I would expect, the flash isn't working... I Will try to install the Adobe Flash Plug-in, and see what happens...

other flash related installed packages:

[LIST]
[*]Ubuntu restricted extras
[*]libswfdec-0.8-0 (SWF (Macromedia Flash) decoder library)
[*]libming1 (Library to generate SWF (Flash) Files)
[*]Commonly used restricted packages for Ubuntu
[/LIST]


Stop!  No don't install the Adobe Flash Plug-in....because mine isn't selected.  The "sudo seven.... does it in a special way and if you try to do it in Ubuntu software centre you'll be back to square one!

I don't have libswfdec....etc installed, nor libming1 but I do have commonly.... and Ubuntu restrict.....

Just uninstall all the flash stuff, shut down and reboot and then install the "sudo ...." that I mentioned originally and try again.....I know it is a pain but it is best to start from scratch and try again.....I did have the same problem as you and uninstalled flash related stuff and did the "sudo ....etc" rebooted and it worked for me and it is still working...

---

### Post by NarfZilla on 2010-05-12
I did everything as you said, but the problem remains...

but I realized that this happens when I close FireFox...

any clues?

thanks

---

### Post by clevertomato on 2010-05-13
Thanks EllyBilateralCl. I tried and tried, but I couldn't get Flash installed in Lucid even though I've done it many times in previous releases. Your tip worked for me, although I wish I understood why.

What worked:

```
sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get  update && sudo apt-get install flashplugin64-installer
```

---

### Post by lavinog on 2010-05-13
> **shawnboy said:**
> Thanks EllyBilateralCl. I tried and tried, but I couldn't get Flash installed in Lucid even though I've done it many times in previous releases. Your tip worked for me, although I wish I understood why.

What worked:

```
sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get  update && sudo apt-get install flashplugin64-installer
```

This adds a PPA to your repository sources (unofficial source)
```

sudo add-apt-repository ppa:sevenmachines/flash

```

```

sudo apt-get update

```
refreshes the package listing with the new repository

```

sudo apt-get install flashplugin64-installer

```
installs the package from the ppa

joining commands with "&&" like:
```

command1 && command2 && command3

```
means do command1, then do command2 only if command1 completed successfully, then do command3 if command2 completed successfully.

command1 || command2 means only do command2 if command1 fails.

---

### Post by EllyBilateralCI on 2010-05-13
> **NarfZilla said:**
> I did everything as you said, but the problem remains...

but I realized that this happens when I close FireFox...

any clues?

thanks

When you installed, did you have firefox open at the time?

Well anyway, I'm wondering if you could do this one more time but this time uninstall everything using the method below BUT please don't have Firefox open - in fact close everything and only have the Terminal open ....

sudo apt-get purge flashplugin-nonfree flashplugin-installer gnash gnash-common mozilla-plugin-gnash swfdec-mozilla    

and then .....

sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer

Fingers crossed! Please do let me know the outcome....

---

### Post by NarfZilla on 2010-05-13
Nothing... The first time it worked, but after firefox was closed, same thing happens...

:(

---

### Post by EllyBilateralCI on 2010-05-13
> **NarfZilla said:**
> Nothing... The first time it worked, but after firefox was closed, same thing happens...

:(

Ok, you've got it installed then...try this but remember firefox has to be closed and all other applications just to be sure that nothing interferes with it...

sudo mv libflashplayer.so /usr/lib/flashplugin-installer/libflashplayer64.so

Again, please let me know....

---

### Post by NarfZilla on 2010-05-13
I did so, and still no... (the Ffox was closed although) 

Sorry for wasting your time :/

---

### Post by EllyBilateralCI on 2010-05-13
> **NarfZilla said:**
> I did so, and still no... (the Ffox was closed although) 

Sorry for wasting your time :/

Ok do this with the Ffox closed and all other applications as well....
sudo update-alternatives --install /usr/lib/mozilla/plugins/flashplugin-alternative.so xulrunner-addons-flashplugin /usr/lib/flashplugin-installer/libflashplayer64.so 60then 

sudo update-alternatives --config xulrunner-addons-flashplugin

then re-start Ffox and go to Tools --> Addons - see if flash is there.

Otherwise if Ffox still not showing flash then do the alternative method
which I've googled....

[http://www.blueplastic.net/en/ubuntu-10-04-lucid-lynx-plugin-de-flash-64-bits/](http://www.blueplastic.net/en/ubuntu-10-04-lucid-lynx-plugin-de-flash-64-bits/)

It's the only thing I can think of!

---

### Post by geodanny on 2010-05-13
EllyBilateralCI: is your fix specific to Lucid-64 or does it work with 32 bit as well?  

I have the 32 bit Lucid installed and have the same problems. Sound works on my computer. Flash files, such as on Youtube and elsewhere, do not have sound in FF 3.6.3. I have removed and installed Flash several times. Each time I install it, sound works initially. The next time the computer reboots, I am back to square one and the sound does not work with Flash. I install/remove Flash through the Ubuntu Software Center.

---

### Post by NarfZilla on 2010-05-13
**[SIZE="5"]IT WORKED![/SIZE]** :guitar:

I'm singing this: 
[http://www.youtube.com/watch?feature=related&v=2Z4m4lnjxkY&gl=BR](http://www.youtube.com/watch?feature=related&v=2Z4m4lnjxkY&gl=BR)



The first choice you gave me didn't worked... but the flash installer totally did it! : )

I closed Ffox and removed everything... including everything in .mozilla/plugins - maybe that was the problem...

anyway... I performed some testes, and until now everything is fully working!


Thank You Very Much!

this forum should have a "thumbs up" button, to reward users like you! :)

---

### Post by EllyBilateralCI on 2010-05-13
> **geodanny said:**
> EllyBilateralCI: is your fix specific to Lucid-64 or does it work with 32 bit as well?  

I have the 32 bit Lucid installed and have the same problems. Sound works on my computer. Flash files, such as on Youtube and elsewhere, do not have sound in FF 3.6.3. I have removed and installed Flash several times. Each time I install it, sound works initially. The next time the computer reboots, I am back to square one and the sound does not work with Flash. I install/remove Flash through the Ubuntu Software Center.

By default the flash in Ubuntu Software centre is for 32 bit and so that should suffice.

Ok, we'll start from here and see where we go....

ls /usr/lib/adobe-flashplugin/
ls  /usr/lib/flashplugin-installer/

Put both command lines in the terminal and tell me the outcome of both...

---

### Post by EllyBilateralCI on 2010-05-13
> **NarfZilla said:**
> **[SIZE=5]IT WORKED![/SIZE]** :guitar:

I'm singing this: 
[http://www.youtube.com/watch?feature=related&v=2Z4m4lnjxkY&gl=BR](http://www.youtube.com/watch?feature=related&v=2Z4m4lnjxkY&gl=BR)



The first choice you gave me didn't worked... but the flash installer totally did it! : )

I closed Ffox and removed everything... including everything in .mozilla/plugins - maybe that was the problem...

anyway... I performed some testes, and until now everything is fully working!


Thank You Very Much!

this forum should have a "thumbs up" button, to reward users like you! :)

Oh that's FANTASTIC NEWS!!!  Phew! I'm so relieved! \\:D/

---

### Post by Randy Winchester on 2010-06-11
> **Scibax said:**
> The problem is not flash player at all.  Ubuntu enables desktop effects by default and it seems to have an issue in this iteration.  

Way too strange... I spent a couple hours yesterday fiddling with things trying to get Flash 10.1 working with Lucid, and it didn't start working until after I turned desktop effects ON.  I've got wobbly windows and everything, and Flash is finally working!  

Just another data point.  It appears that having effects on doesn't cause the Flash problem.

The only problem now is getting audio from YouTube.  The Flash plugin in Mozilla opens up 10 ALSA connections, all turned all the way up, and I still don't get the sound.

---

### Post by Automat2 on 2010-06-11
I had Flash-Aid installed but it didn't play embedded Flash videos on Lucid 64bits. Then I tried 

> sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer

It didn't work until I removed Flash-Aid.

Now it seems ok. I've restarted Ubuntu and FF.

---

### Post by Alphinor on 2010-07-19
Hi!! I also had some issues with flash working but not completely working and I found another solution which is quite easy (though maybe a little twisted)

I noticed that when I was trying out linux mint (based on ubuntu) everything worked just fine. But I didn't like it much so I tried installing their modified version of flash (don't ask me what the difference is, I have no idea) on lucid and it worked just fine after removing every other flash I had installed first...

So if you want to try it out, it's easy, you can find a .deb file here [http://packages.linuxmint.com/pool/import/m/mint-flashplugin-x64/](http://packages.linuxmint.com/pool/import/m/mint-flashplugin-x64/)

just remove everything else, and install this one, worked just fine on my installation of lucid lynx!

---

