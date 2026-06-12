---
title: "Do not update to 195.36.08! - nvidia"
date: 2010-03-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kurros on 2010-03-06
An update was pushed today for lucid to update nvidia-graphics-drivers to 195.36.08. Nvidia has pulled this update as there are possibly severe issues with fan speed control causing cards to overheat and cause permanent damage.

> We are aware that some customers have reported fan speed issues with
the latest 196.75 WHQL drivers on NVIDIA.com. Until we can verify and
root cause this issue, we recommend that customers stay with, or return
to 196.21 WHQL drivers. Release 196.75 drivers have been temporarily
removed from our website.

> We believe recent NVIDIA UNIX graphics drivers, 195.36.08 and 195.36.03, are also affected by this. Until the problem is resolved, we recommend that UNIX users revert to the 190.53 web release or the 195.30 public beta.

We are in the process of removing 195.36.08 and 195.36.03 from NVIDIA's FTP site.

We will post more information as it is available.

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)


A good idea to pin before updating or rolling back the nvidia debs if you have.

---

### Post by ToxicBurn on 2010-03-06
yeah I spoke to support and they told me the issue should be fixed with-in a week 
 
so hold off for a bit we dont want to go burning peoples GPU's lol

---

### Post by infoseeker on 2010-03-06
I have 195.36.08 installed and running and my GPU temperature seems to be fine (no change from before the update).  I will keep my eye on it tho.

Thanks

---

### Post by _R2D2_ on 2010-03-06
Meanwhile, nouveau's developers ask Linux T. to exclude their stuff from the kernel :D
[http://lkml.org/lkml/2010/3/5/196](http://lkml.org/lkml/2010/3/5/196)

---

### Post by Atermoon on 2010-03-06
Ugh... already updated. What makes it even worse is that I can't find a way to monitor my card's temp.

---

### Post by gradinaruvasile on 2010-03-06
> **Atermoon said:**
> Ugh... already updated. What makes it even worse is that I can't find a way to monitor my card's temp.

Install nvclock. The graphic interface is called with nvclock_gtk. Else, in a terminal 

run nvclock -T

It may not support most recent cards.

---

### Post by cookiecruncher on 2010-03-06
> **Atermoon said:**
> Ugh... already updated. What makes it even worse is that I can't find a way to monitor my card's temp.

Have you tried 'nvidia-settings' in terminal?  It's under 'Thermal Settings'.

---

### Post by Atermoon on 2010-03-06
> **cookiecruncher said:**
> Have you tried 'nvidia-settings' in  terminal?  It's under 'Thermal Settings'.

Can't find Thermal Settings anywhere (see below) :|

---

### Post by Atermoon on 2010-03-06
> **gradinaruvasile said:**
> Install nvclock. The graphic interface is called with nvclock_gtk. Else, in a terminal 

run nvclock -T

It may not support most recent cards.

```
nvclock -T
Error: temperature monitoring isn't supported on your videocard.
```

Ok that explains it.

---

### Post by lem79 on 2010-03-06
Running 195.36.08 here on Ubuntu 9.10 AMD64 with a GTX260. GPU temperature was fine until after suspend/resume just now (hadn't noticed it with previous suspend/resumes).

The air coming out the back of the GPU card doesn't feel too hot, and the fan speed is fairly low. GPU clocks are 300/100MHz (core/mem). Running compiz but infrequent effects.

Ambient temp is about 22C, ambient GPU temp 43C, GPU core 82C (as reported by nvidia-settings).

Might downgrade to see if the air temp feels different.


-------------------------------------

Ok, just downgraded to 195.30, no rebooting. Logged out, switched to VT, stopped GDM, ran the nVidia installer script, modprobe nvidia, started GDM, logged back in.

Air coming out the back of the GPU felt the same temperature, same fan speed. Temperature is reading 30C lower @ 52C.

So, ambient air temp same @ 22C, GPU ambient temp 45C, GPU core temp 52C (30C LOWER than reported by 196.36.08, yet only 2-3 minutes has elapsed).


What's going on here? Is it just a case of the driver reporting the GPU core temperature incorrectly? The air felt the same coming out the back of the GPU, but the temp read 30C lower?

---

### Post by exploder on 2010-03-06
I appreciate the information! I have a brand new nvidea gt 220 and sure would hate to fry it! I will stick with the open source drivers for the time being. Thanks!

---

### Post by cookiecruncher on 2010-03-06
Mine has thermal settings.

---

### Post by dyltman on 2010-03-06
Snap, so that's why I have been having problems. Hopefully it ain't fried yet.

---

### Post by Ichtyandr on 2010-03-06
I updated to latest nvidia-current, GeForce 8400 GS here and thermal settings show core temperature 51 C, which I guess is normal

---

### Post by reddawg60 on 2010-03-06
From what I have read this driver only causes overheating while using 3D applications (i.e. games).  
 

 [http://games.slashdot.org/article.pl?sid=10/03/05/0739241](http://games.slashdot.org/article.pl?sid=10/03/05/0739241)

---

### Post by dino99 on 2010-03-06
no problem with my fanless card  :lolflag:

---

### Post by gradinaruvasile on 2010-03-06
> **exploder said:**
> I appreciate the information! I have a brand new nvidea gt 220 and sure would hate to fry it! I will stick with the open source drivers for the time being. Thanks!

You can safely use the 195.30. I use it since it appeared on 4 computers and nothing happened - on one computer is a gf 210, a lower speed version of 220 (the others: 7600gs, 8200 IGP, Quadro 135M - notebook).

I googled around and as i observer high end cards fried (8800 and the like) using the 196.75 driver on Windows. Most of them were playing games on them.
The nvidia devs pulled the 195.36.08 driver because some changes were similar to 196.75. 

The main problem, it seems, is with the cards automatic fan control profiles - that is, the fan doesnt start when the card reaches a given temperature. Some reported that setting the card to a specific profile the fan was working.

No one using Linux complained (yet) AFAIK.

And the fanless cards shouldnt have any problems. But it is better to be safe than sorry...

---

### Post by chrisccoulson on 2010-03-06
From the ubuntu-devel list a short while ago:

> Hi all,

According to Nvidia, drivers 195.36.08 (i.e. the current driver in the
archive) and 195.36.03 might be affected by the same GPU fan speed
issues which affect the Windows driver:
[http://www.nvnews.net/vbulletin/announcement.php?a=39](http://www.nvnews.net/vbulletin/announcement.php?a=39)

I have been using these drivers for while now without experiencing
that problem but, if you want to be on the safe side, I suggest that
you temporarily switch to the open driver until we're sure that the
problem is fixed. In order to do so you can follow either point 1 (the
easy way) or point 2:

1) Disable the driver with Jockey (the restricted drivers manager) and
restart your computer.

OR

2) Open the terminal and type the following commands:
sudo update-alternatives --config gl_conf (and select the alternative
provided by mesa)
sudo ldconfig
sudo update-initramfs -u
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_old

and restart your computer.


Sorry for the inconvenience, I'll keep you posted on the issue.

Regards,

-- 
Alberto Milone
Sustaining Engineer (system)
Foundations Team
Canonical OEM Services

---

### Post by gradinaruvasile on 2010-03-06
And this applies to Ubuntu 10.04 only, i suppose? You should have pointed that out. those who use Lucid should know that it can break stuff.

Those who are using the nvidia drivers 195.36.0x downloaded from the site, just download 195.30 and install it.

And those who are using PPAs with 195.36.0x should disable them and reinstall the nvidia drivers from the repos for the time being. 

The stock Karmic drivers from the repos are 185 series, not affected by this bug.


BTW:
This means losing:

3d acceleration -> no more compiz, 3d games, anything that uses OpenGl acceleration
xv playback, vdpau -> tearing movies (absolutely no HD), 
extremely slow flash + CPU hogging -> crappy web browsing experience

---

### Post by chrisccoulson on 2010-03-06
> **gradinaruvasile said:**
> And this applies to Ubuntu 10.04 only, i suppose? You should have pointed that out.


This is posted in the "Lucid Lynx Testing and Discussion" section and the version number of the affected package is provided, so I didn't think there'd be any need to point out that it affects Lucid

---

### Post by dyltman on 2010-03-06
> **reddawg60 said:**
> From what I have read this driver only causes overheating while using 3D applications (i.e. games).  
 

 [http://games.slashdot.org/article.pl?sid=10/03/05/0739241](http://games.slashdot.org/article.pl?sid=10/03/05/0739241)

Yeah, I've had this problem for a while that my screen turns black for a while and then becomes normal when having the driver installed on ubuntu and running on windows (removing ubuntu no longer causes this for some insanly strange reason).

And on ubuntu my computer suddly get's laggy and messed up until I reboot.

---

### Post by gradinaruvasile on 2010-03-06
Because many use PPAs or install the nvidia drivers from the nvidia site. And they are using different Ubuntu versions.

Maybe this thread should be visible in other main sections too as it affects other versions too...

---

### Post by SirBismuth on 2010-03-06
Am running these drivers without an issue so far, see attachment, GPU Temp is 57c and Fan Speed 30%.  Don't know what it was before upgrading, but this seems ok?.

B

---

### Post by nanog on 2010-03-06
> 3d acceleration -> no more compiz, 3d games, anything that uses OpenGl acceleration
xv playback, vdpau -> tearing movies (absolutely no HD), 
extremely slow flash + CPU hogging -> crappy web browsing experience

Not if nouveau + gallium works better on your nvidia card than the binary driver ever did!

---

### Post by Technoviking on 2010-03-06
Sticky a warning for folks.

Thanks,
T-V

---

### Post by autocrosser on 2010-03-06
You can always set a manual speed for the card--I noticed my cards (SLI) were running at 30%--I use NVclock, so I just bumped my fan speeds to 50%--they are both running about 44c, so I'm OK with it. I monitor my temps, so I'll keep a eye on things........

---

### Post by jerrrys on 2010-03-06
i was going to upgrade today; glad i ran across this...

---

### Post by Uncle Spellbinder on 2010-03-06
Unfortunately, I already updated. Running 195.36.08. Not seeing any issues at all so far. 

* keeps fingers crossed *

---

### Post by ratcheer on 2010-03-06
> **Uncle Spellbinder said:**
> Unfortunately, I already updated. Running 195.36.08. Not seeing any issues at all so far. 


Same, here. I have been watching the temp and it is holding at around 46C. I am very comfortable with that.

I don't run much graphics intensive software, though.

Tim

---

### Post by edkmho on 2010-03-08
Dear all,

I have upgrade to 195.36.08 and had been running Lucid box for the whole and without compiz enable the temperature was holding on 37C. but once i enable compiz the temperature will steadily climb to 49C in a matter of 30 minutes. 

I am no linux geek and find it difficult to downgrade to 190.x driver, as i installed this 195.36.08 by selecting from the update manager.

By the way, my video card is Gigabyte GT240 (GV-N240D3-1GI).

Will keep the box running for monitoring purposes. Hope that nvidia will come out with the solution soon.

---

### Post by dabl on 2010-03-08
I had already installed 195.36.08 on my Debian sid system, and then installed Kubuntu 10.04 on Friday and installed 195.36.08 on that too, all before "the word" came from Nvidia.  I've got a conky that shows GPU temps, and I've been watching it closely since the concern about the thermal control & fans came out.  I see no indication of any problem -- GPU temp has not been above 47C, even with compiz or desktop effects active and Googleearth running.  Feels like the bullet missed my GTX260.

---

### Post by phenest on 2010-03-08
I was running Lucid with the 195.36.08 driver with no problems. I'm now using the same driver from nVidia in Debian Squeeze. Running at 54 degrees which is normal for my GeForce 7950GTX. I'm now running Lucid in a VM, so I can't report on that any more.

---

### Post by Sam on 2010-03-08
I have the 195.36.08 driver on lucid with a GeForce 7600 GS. It's fanless, so I do not worry at all about this fan issue. \\:D/

---

### Post by ratcheer on 2010-03-08
> **Sam said:**
> I have the 195.36.08 driver on lucid with a GeForce 7600 GS. It's fanless, so I do not worry at all about this fan issue. \\:D/

The fan is not the real issue, it is just a symptom of the issue, which is the GPU running excessively hot. The fan runs hard to try to keep it cool. If the GPU runs too hot for too long, it will self-destruct.

Tim

---

### Post by kernco on 2010-03-08
> **edkmho said:**
> I have upgrade to 195.36.08 and had been running Lucid box for the whole and without compiz enable the temperature was holding on 37C. but once i enable compiz the temperature will steadily climb to 49C in a matter of 30 minutes. 

This seems normal to me.  It's expected that any video card will run hotter when doing more work.  49C is a fairly normal and safe temperature I think.

---

### Post by kernco on 2010-03-08
> **ratcheer said:**
> The fan is not the real issue, it is just a symptom of the issue, which is the GPU running excessively hot. The fan runs hard to try to keep it cool. If the GPU runs too hot for too long, it will self-destruct.
I think you have this backwards.  My understanding of the bug is that the fan does not run at the correct speed, and as a result the cards overheat.

---

### Post by ratcheer on 2010-03-08
> **kernco said:**
> I think you have this backwards.  My understanding of the bug is that the fan does not run at the correct speed, and as a result the cards overheat.

I guess you could be right. If the fan is running too slowly, it could work that way. I will try to find some definitive info.

Thanks,
Tim

---

### Post by phenest on 2010-03-08
> **ratcheer said:**
> I guess you could be right. If the fan is running too slowly, it could work that way. I will try to find some definitive info.

Thanks,
Tim

Read the top of the page in post #1's link. The overheating is due to poor fan speed control.

It could be that those of use that haven't found this to be a problem, are not giving our GPU's much to do. I'm running Gnome Shell at best. Haven't played a game for ages. But I think I'll downgrade to be on the safe side.

---

### Post by autocrosser on 2010-03-08
I'm running a SLI system & run UT2004---so I'm just using the Nvidia settings to raise the fan speed whilst I'm gaming---no problems here---I find that if I boost my fan speed to 50% the temps run lower than they were with prior drivers........

---

### Post by hikaricore on 2010-03-09
<< Fanless.

muhahahaha

---

### Post by edkmho on 2010-03-10
Hi Autocrosser,

may i know how you change the temperature control in nvidia-settings?

Thanks.

---

### Post by jmexia on 2010-03-11
Hi All,

Any idea when the revised driver is going to be released?

Thanks,
J.

---

### Post by Otaconda on 2010-03-11
Is there a bug on launchpad for this?

---

### Post by gradinaruvasile on 2010-03-11
No one knows. Check the nvnews forum:

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by FuturePilot on 2010-03-17
This has been fixed. See [http://www.nvnews.net/vbulletin/showthread.php?p=2209577]("http://www.nvnews.net/vbulletin/showthread.php?p=2209577") But I noticed the version in the repos is still 195.36.08. Are there plans to update it to the fixed version?

---

### Post by samjh on 2010-03-21
The driver in the repos seem to be the fixed version now:
[http://packages.ubuntu.com/lucid/nvidia-current](http://packages.ubuntu.com/lucid/nvidia-current)

---

### Post by peacewithall on 2010-03-21
Not sure if it's cooincidence, but I decided to give the new 'fixed' driver a try (195.36.15), on my Ubuntu 9.10, using my 9800GT. I saw the driver had been released on NVNews.net on the 15th, and it made official release on the 19th March.

Anyway I installed the driver on the 15th, I noticed the fan going faster than usual (pretty loud infact), card was hotter (74C maxed at) too but I thought with the weather warming up it's to be expected, also the drivers fixed right?, so nothing to worry about. Anyway on the 19th, I started a game using WINE, all seemed OK for say 10 minutes then my screen flashed, and became covered with artifacts and then froze, my entire system then became unresponsive, I hard reset, artifacts were present during post screen too, so I turned my system off entirely and gave it 5 minutes, I restarted and post screen seemed normal again, and to be safe I booted into Windows 7 (which still had the older '196.21' driver installed), I logged in, and 2 minutes later screen corruption and then my system locked up. I turned off, retried the default proprietary driver with Karmic, same thing, as a last resort, I borrowed from a friend an Nvidia 7600, booted up and my systems as it was, games all working as usual, so my 9800GT *is* dead.

My point is I've had my 9800GT for a little under 1 1/2 years, I don't overclock, but the card is an OC edition, its been working fine all that time then days after installing this driver its dead?, maybe it is cooincidence, but it really doe's make me think, the driver after a potentially damaging driver, and days after my cards dead?.

I think most people have replied the faulty driver worked fine with them, so maybe it is just cooincidence.

---

### Post by Perfect Storm on 2010-03-21
I had the same problem and symptoms as you did peacewithall. I fried my 8800 GTX card.
So I had to buy a new card (GTX 285 1GB).

---

### Post by plun on 2010-03-21
> **peacewithall said:**
> 

My point is I've had my 9800GT for a little under 1 1/2 years, I don't overclock, but the card is an OC edition, its been working fine all that time then days after installing this driver its dead?, maybe it is cooincidence, but it really doe's make me think, the driver after a potentially damaging driver, and days after my cards dead?.


Well, this is the way to file a bug against a closed nVidia driver.

I don't think your card is "fried"....

> 4a) Please always include a copy of an nvidia-bug-report.log file, which can be generated with the `nvidia-bug-report.sh` script shipped with the NVIDIA Linux/FreeBSD graphics drivers and installed in your PATH; the log file will be placed in the current working directory. Newer versions of the script will automatically compress the log file renaming it to nvidia-bug-report.log.gz.

To make sure this log file includes as much relevant information as possible, please start the X server with `startx -- -logverbose 6` and run `nvidia-bug-report.sh` after the problem has occurred. If X can not be started or the machine appears to have crashed, please check if you can log into it remotely (e.g. via ssh or telnet) and run `nvidia-bug-report.sh` in the remote shell, if possible.

If the machine can not be logged into remotely, please run the bug report script with X running (this will ensure that data points only available when the device is initialized, such as the VBIOS revision, are captured in the log file). All requests for assistance from NVIDIA must include the bug report, per the instructions above.

Ref:
[http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678)

---

### Post by Sockerdrickan on 2010-03-21
If you want to install the .15 driver manually, I doesn't work with Ubuntus vanilla kernel, I used the -rt kernel if that helps someone

---

