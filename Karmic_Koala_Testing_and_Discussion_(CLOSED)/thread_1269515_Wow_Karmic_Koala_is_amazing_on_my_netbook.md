---
title: "Wow Karmic Koala is amazing on my netbook"
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Foxray on 2009-09-18
I just upgraded to Karmic Koala alpha 6 on my Dell Mini 9 netbook due to some issues with the wireless connectivity and avi video stuttering on my fresh install of Jaunty 9.04. I've gotta say, wow what a difference. Avi video stuttering has completely disappeared (I think its the UXA acceleration thats replacing the EXA method in xorg), and my wireless connection connects to my router amazingly fast (compared to my dellbuntu hardy, and UNR Jaunty).

Only a couple issues at bootup, the udevd seems to have some extra lines that it did not need, no biggie, just warnings not crashes. CUPS isn't working, that crashed but its already a reported issue and I don't print from my netbook anyway. All in all I'm pretty impressed how fast it boots to a usable desktop. Can't wait for next month when Karmic is released officially.

---

### Post by derrick81787 on 2009-09-18
Yeah, I just upgraded my Dell Mini 9 for the fun of it.  I liked UNR on Jaunty, but on Karmic, it's just beautiful.  I get the same crashes you mentioned, but I'm sure they'll be fixed by the time it gets released.  Other than that, I pretty much like everything about it.

---

### Post by victor9098 on 2009-09-18
I have been running Karmic UNR since the Alpha 5 on an Advent 4211 netbook and must admit it looks and runs all much smoother. Sure there have been bugs, but we are still in Alpha territory. All in all I am really looking forward to the final version.

Using the hanso theme but would like to see some new wallpapers!

---

### Post by cororok on 2009-09-18
I'm using eeepc 1000H. I couldn't use Wireless WAP2 on ubuntu9.04 but now it works well on 9.10.
and the response speed of the graphics is very fast.

because Atom CPU of netbook is slow, firefox3.5 response slowly.
so I changed it to chrome. it's really fast but doesn't support Flash yet.

you can donwnload it.

[http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel)

speed :   chrome >>>>>> firefox on netbook.

---

### Post by zekopeko on 2009-09-18
> **cororok said:**
> I'm using eeepc 1000H. I couldn't use Wireless WAP2 on ubuntu9.04 but now it works well on 9.10.
and the response speed of the graphics is very fast.

because Atom CPU of netbook is slow, firefox3.5 response slowly.
so I changed it to chrome. it's really fast but doesn't support Flash yet.

you can donwnload it.

[http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel)

speed :   chrome >>>>>> firefox on netbook.

There is a ppa with daily builds of chromium. The flash support is at this moment a little finicky but it works (I'm having problems mainly with using controls on Youtube ie. they don't work, clicking etc.)

---

### Post by andrewabc on 2009-09-18
Intel video drivers are supposed to be fixed and much faster. 9.04 had bad intel drivers apparently. So that got fixed, along with new intel driver technologies (UXA).

If you have ext4 instead ext3 you might notice some speed increases as well.

Glad to hear it is working good on netbooks. Going to buy one sometime.

---

### Post by mikedep333 on 2009-09-18
Yeah, Karmic runs very overall well on my brand new (intel-centric) netbook (which is not technically a netbook.)
[http://www.amazon.com/Acer-Aspire-AS1410-8414-11-6-Inch-Sapphire/dp/B002LEXA64](http://www.amazon.com/Acer-Aspire-AS1410-8414-11-6-Inch-Sapphire/dp/B002LEXA64)
I am not using the netbook remix because it doesn't have an atom processor, and I am under the impression that UNR requires that.

Still, here's what I love:
1. Most hardware hardware *just works* TM
2. Beautiful new boot screen (when it works.)
3. Overall stable for an alpha
4. Fast, even with desktop effects
5. New sound config utility
6. New disk utility by default
7. Nice new version of Deluge Torrent in repos
8. UPnP for gnome vnc remote desktop server
9. VLC 1.0
10. Network-Manager is improved
11. New Login Screen shows battery status

Here's what I'm disappointed in:
1. Youtube controls kind of buggy, can't play back HD youtube videos from the flash applet well on my Core 2 Solo @ 1.4 ghz
2. Savage XR (3d game) won't startup, and nexuiz has no character/gun models rendered
3. Poor battery life
4. Trouble viewing a large workgroup on the network, often asks for a password, may be trouble with a Windows 7 homegroup
5. "cheese" webcam utility not installed by default. More people use it than evolution.
6. Wi-Fi switches to like 1 megabit/second (or less) every so often. I'm using the intel 4965AGN, which should be very common.

Anyway, in summary, I have high hopes for this release.

---

### Post by steev182 on 2009-09-18
UNR Alpha 5 is on my mini 9. It was pretty easy to figure out everything and get it how I want.

Firefox is still a bag of bolts on here, so I followed the advice of putting Chromium on, and boy, I played 2 youtube videos (Osi Uminyera's Touchdown against the Redskins and the trailer to Away We Go) and the played perfectly with no stutters.

Ubuntuone doesn't let me add my computer, so I will keep my fingers crossed that it will when I install Alpha 6...

The UNR interface is so much nicer than before, I'm not too sure about empathy still though.

---

### Post by andrewabc on 2009-09-18
> **mikedep333 said:**
> 
I am not using the netbook remix because it doesn't have an atom processor, and I am under the impression that UNR requires that.


I know nothing about UNR, but it should work with your intel processor. Try a livecd.

It's like how moblin is designed for atom processor, yet works fine on my 3 year old core2duo desktop. (need SSE3 capable processor)

Also, transmissionbt has much more updates than deluge according to changelogs since jaunty.

---

### Post by mikedep333 on 2009-09-19
> **andrewabc said:**
> I know nothing about UNR, but it should work with your intel processor. Try a livecd.

It's like how moblin is designed for atom processor, yet works fine on my 3 year old core2duo desktop. (need SSE3 capable processor)

Also, transmissionbt has much more updates than deluge according to changelogs since jaunty.


[http://www.ubuntu.com/GetUbuntu/download-netbook](http://www.ubuntu.com/GetUbuntu/download-netbook)
It says UNR requires an atom processor. Last time I checked there was some hardware configuration stuff specific to atom netbooks.

I use deluge because it features blocklists (via a plugin.)

> **steev182 said:**
> UNR Alpha 5 is on my mini 9. 

...

Ubuntuone doesn't let me add my computer, so I will keep my fingers crossed that it will when I install Alpha 6...

Reinstalling could help, but most likely you will be fine doing the regular updates to advance from Alpha5 to post-Alpha6.

---

### Post by andrewabc on 2009-09-19
> **mikedep333 said:**
> [http://www.ubuntu.com/GetUbuntu/download-netbook](http://www.ubuntu.com/GetUbuntu/download-netbook)
I use deluge because it features blocklists (via a plugin.)

Just so you and others know, I wasn't trying to say one is better than the other.
Looking at changelogs for each, transmission has had about 5x more development than deluge since what is included in jaunty. Next deluge version is only 1/2 complete and hasn't had new version out since June 15. So development has slowed down a lot.


transmission with jaunty 1.51. Currently with karmic 1.74 (hopefully 1.75)
[http://trac.transmissionbt.com/wiki/Changes#version-1.75](http://trac.transmissionbt.com/wiki/Changes#version-1.75)

deluge with jaunty 1.1.6. Currently with karmic 1.1.9
[http://dev.deluge-torrent.org/wiki/ChangeLog](http://dev.deluge-torrent.org/wiki/ChangeLog)

Not much has changed for deluge compared to transmission. Good thing I guess for people who use transmission and anyone who would be using default installed torrent program.

---

### Post by pjalegria on 2009-09-19
Hi

Im runing Jaunty UNR on mine Acer Aspire One, how can i upgrade to Karmic UNR???:lolflag:


Thanks

---

### Post by Longinus00 on 2009-09-19
> **mikedep333 said:**
> I use deluge because it features blocklists (via a plugin.)

In Transmission you can use a blocklist without even installing a plugin.

[http://trac.transmissionbt.com/wiki/Blocklists](http://trac.transmissionbt.com/wiki/Blocklists)

---

### Post by mikedep333 on 2009-09-19
> **pjalegria said:**
> Hi

Im runing Jaunty UNR on mine Acer Aspire One, how can i upgrade to Karmic UNR???:lolflag:


Thanks

Assuming you understand the risk of upgrading to an ALPHA release, these are the instructions:

[http://www.ubuntu.com/testing/karmic/alpha6](http://www.ubuntu.com/testing/karmic/alpha6)

> To upgrade from Ubuntu 9.04 on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '9.10' is available. Click Upgrade and follow the on-screen instructions.
If Alt+F2 doesn't work, you can enter "update-manager -d" in gnome terminal.

---

### Post by andrewabc on 2009-09-19
> **pjalegria said:**
> Hi

Im runing Jaunty UNR on mine Acer Aspire One, how can i upgrade to Karmic UNR???:lolflag:


Thanks

You probably want to wait until final release.
But I do recommend downloading alpha 6, putting it on USB stick and booting into it to see what works and what does not work for you. I don't recommend installing it unless you don't mind the chance of having to format several times if OS breaks.

---

### Post by mikedep333 on 2009-09-20
> **Longinus00 said:**
> In Transmission you can use a blocklist without even installing a plugin.

[http://trac.transmissionbt.com/wiki/Blocklists](http://trac.transmissionbt.com/wiki/Blocklists)

Cool, thanks.

BTW, Deluge ships with the blocklist plugin by default. But since transmission is liter, I will use that on Linux and Mac. Deluge, being available for windows, will remain my windows BT client.

---

### Post by cylverbak on 2009-09-20
I'm running the alpha6 on my EeePC1000 and it's working very well. My bluetooth mouse and wifi with WPA2 are working. Other hardware doesn't appear to be a problem. Graphics are sharp and beautiful.

I am torn with the menu-ing system. I seem to be using more clicks than I'm used to in Eeebuntu 3 NBR to get to where I want to go. It does look tidier though.

My only complaint at the moment is being forced into maximised windows. Please, please tell me there is a setting somewhere that I can chose to open un-maximized by default. Doing it on a window by window basis now is a major pain :)

I'm really looking forward to the final in October.

---

### Post by zekopeko on 2009-09-20
> **cylverbak said:**
> I'm running the alpha6 on my EeePC1000 and it's working very well. My bluetooth mouse and wifi with WPA2 are working. Other hardware doesn't appear to be a problem. Graphics are sharp and beautiful.

I am torn with the menu-ing system. I seem to be using more clicks than I'm used to in Eeebuntu 3 NBR to get to where I want to go. It does look tidier though.

My only complaint at the moment is being forced into maximised windows. Please, please tell me there is a setting somewhere that I can chose to open un-maximized by default. Doing it on a window by window basis now is a major pain :)

I'm really looking forward to the final in October.

Alt+F2
gconf-editor
/apps/maximus

either add to the list the windows class/name of the application that you don't want to have maximized or click no-maximize or some such option.

---

### Post by seamuso on 2009-09-20
> **cylverbak said:**
> I'm running the alpha6 on my EeePC1000 and it's working very well. My bluetooth mouse and wifi with WPA2 are working. Other hardware doesn't appear to be a problem. Graphics are sharp and beautiful.

I am torn with the menu-ing system. I seem to be using more clicks than I'm used to in Eeebuntu 3 NBR to get to where I want to go. It does look tidier though.

My only complaint at the moment is being forced into maximised windows. Please, please tell me there is a setting somewhere that I can chose to open un-maximized by default. Doing it on a window by window basis now is a major pain :)

I'm really looking forward to the final in October.


If you're using the classic desktop, disable maximus in the startup apps

---

### Post by cylverbak on 2009-09-20
Thanks guys, that did it! I disabled Maximus in Startup - problem solved. I'll play with Maximus settings now that I know that it can be done so I may be able to fine-tune settings as I get more familiar with this system.

---

### Post by pjalegria on 2009-09-20
How can you acess maximus settings???

---

### Post by cylverbak on 2009-09-20
See zekopeko's post - #18 in this thread.

After opening a terminal screen with Alt+F2, type in gconf-editor and navigate into apps and then down to maximus. There appear to be four different settings that you can change. Haven't had time to play with them yet. Good luck.

---

