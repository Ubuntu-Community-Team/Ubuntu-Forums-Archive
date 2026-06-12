---
title: "cannot connect to wifi with LUCID Beta 1"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by eltonw on 2010-03-24
I downloaded the Lucid Beta 1 and booted from the DVD. However, I am unable to connect, and (my apologies) I can't seem to find:confused: a specific forum _for the discussion of the beta_. Could someone kindly point me in the correct direction where I may report this? Machine is an Asus EEE 1000 PC, currently running Karmic 9.10, which can connect, but keeps trying and sending me back to the Authentication dialog when I run the Lucid beta DVD as a "live CD".

---

### Post by chili555 on 2010-03-24
[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

---

### Post by eltonw on 2010-03-24
> **chili555 said:**
> [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)
Thank you for your help. I suspected that the Lucid Beta discussion might be in Development and Programming... and it's right the top of the forum. Lesson learned: don't try going into any forum discussion with an empty stomach (= empty head)!:p

---

### Post by shindou01 on 2010-03-24
Did you try to install drivers for the wifi adapter?I had the same problem which was resolved right after i downloaded and installed drivers from jockey..

---

### Post by eltonw on 2010-03-26
> **shindou01 said:**
> Did you try to install drivers for the wifi adapter?I had the same problem which was resolved right after i downloaded and installed drivers from jockey..
No, I didn't. ... and WHY would I need to do so? I have installed / run previous versions of EEEbuntu, Easy Peasy, and currently running Karmic NBR, I didn't have any need to install drivers for the RaLink RT2860 in my Asus EEE PC. 

It makes no sense that I would now need drivers for the newer iteration of Ubuntu:???:
I could try doing so, but *if this is the case* it is a step **backwards** by Ubuntu WRT hardware support.

---

### Post by cariboo on 2010-03-26
By saying you ae unable to connect, what exactly is happening, do you see access points when you left click the network-manager icon? Can you connect to an access point but not to anything else?

---

### Post by eltonw on 2010-03-27
> **cariboo907 said:**
> By saying you ae unable to connect, what exactly is happening, do you see access points when you left click the network-manager icon? Can you connect to an access point but not to anything else?
_HERE are the steps that I did:_:!:

1) Boot Lucid Lynx Beta 1 DVD

2) Select "Try Ubuntu-Netbook 10.04"

3) Once booted to the desktop, go to Network Manager Applet 0.8
**NOTA BENE:** the following services show a tick mark, indicating that they are ENABLED by default:
Enable Networking
Enable Wireless
Enable Notifications

4) Left click and go through the available list of networks

5) From the list, select {my_network_name}

6) "**Authentication** required for wireless network: Wireless security: WPA & WPA Personal

7) Enter password, and (optionally) "Show password' to ascertain that I HAVE entered the correct password. YES, I  *do* have all CAPS on, because the password I created IS with all caps. 
/REM I am connected to the same network with my Apple Macintosh Powerbook and OS/X 10.6.2. (Snow Leopard)

8) New Keyring Password, Choose password for new keyring

9) I enter a new password and click OK

10)  "**Authentication** required for wireless network: Wireless security: WPA & WPA Personal, Click on Connect button.

11) The connection icon in the Network Manager Applet turns, and turns, and turns for several seconds

12) "**Authentication** required for wireless network: Wireless security: WPA & WPA Personal. THIS dialog pops up again.](*,) _I am still NOT CONNECTED_.](*,)

[FONT=Comic Sans MS][COLOR=DarkRed]WRT installing drivers, the Hardware Drivers app reports: "No proprietary drivers are installed on this system".
[/COLOR][/FONT]
:arrow:YES: I *did* do another burn on a different DVD/R disk *with the same results*.

/REM: This is the third version of Ubuntu NBR that I am using (or trying to use) with my ASUS EEE 1000 PC netback. I previously used EEEbuntu and Easy Peasy both of which easily connect. 
[FONT=Comic Sans MS][COLOR=Red]For some reason _Ubuntu NBR_ has a similar behaviour like the Xandros distro that came with this machine. 
On the ASUS netbook, it _often_ tends to be 'balky" when connecting to a WiFi network.:-(
[/COLOR][/FONT]
COMMENT: I am wondering if Ubuntu has a problem with the following:
Network controller RaLInk RT2860 (Subsystem: RaLink Device 2790)
and / or 
the Ethernet controller Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller       (Subsystem: ASUSTek Device 8324)
This hardware info was obtained using the Sysinfo tool (which seems to be NOT included in the Lucid 1 beta).

So, [COLOR=Red]_if I can NOT connect by wireless to the internet, how may I **properly** and reliably test this beta?_[/COLOR]

NO, I have not tried tethering the netback with a LAN cable to the repeater.

UBUNTU NBR is my PREFERRED distro for the netbook, however, if the connection problem (as it seems) continues to deteriorate with each iteration, I will have to look elsewhere. (I prefer NOT to do so.)


... respectfully,
with cordial greesings from Montreal (Quebec) CANADA.;)

---

### Post by scokem on 2010-03-29
Not gonna be able to add much in the way of insight here, but I too can confirm the Ralink chipsets appear to have gone backwards with Lucid.

I have 3 ralink chips (PC, Laptop and Netbook) and I'm seeing the same as eltonw - the wireless is detected but it won't connect.  I installed the beta on my laptop anyway and once it was installed I was able to get a connection at my workplace (WPA2) but it only stayed connected for awhile (under an hour) and after that I've been unable to reconnect at all - keeps asking for the password even though it's ok.  Same thing happened with my home network (WPA2) - connection worked first time but dropped after 15-20 minutes and keeps requesting the password.  I only ran the live cd on my computer and netbook but they just continuously asked for the WPA password.

Any suggestions on things to try would be welcome.

---

### Post by freakazo on 2010-03-31
I have the exact same problem as the people above, can't connect, same symptons etc.

I've heard that for some people wep or no encryption at all works perfectly, can those who are able to do so test to be sure?

Also is there a bug about this reported and if so can someone please provide me with a link?

---

### Post by eltonw on 2010-03-31
> **scokem said:**
> Not gonna be able to add much in the way of insight here, but I too can confirm the Ralink chipsets appear to have gone backwards with Lucid.

I have 3 ralink chips (PC, Laptop and Netbook) and I'm seeing the same as eltonw - the wireless is detected but it won't connect.  I installed the beta on my laptop anyway and once it was installed I was able to get a connection at my workplace (WPA2) but it only stayed connected for awhile (under an hour) and after that I've been unable to reconnect at all - keeps asking for the password even though it's ok.  Same thing happened with my home network (WPA2) - connection worked first time but dropped after 15-20 minutes and keeps requesting the password.  I only ran the live cd on my computer and netbook but they just continuously asked for the WPA password.

Any suggestions on things to try would be welcome.

This is not very encouraging. [COLOR=Red]**I would like to think the ubuntu developers are watching this thread**[/COLOR]. As I am writing this I am also downloading the respective betas for Easy Peasy and EEEbuntu. Past experiences show that I always could connect with these distros.

Now that Asus has more or less dumped LINUX, I would dare say I am not the only Ausus netbook owner who is looking for an alternative distro. 

[FONT=Comic Sans MS]I hope that the Ubuntu team will address this problem with the RaLink card, _before_ Lucid Lynx is released.[/FONT]

... as for using an unencrypted connection on MY home network: no way! The common default in the various linux distros, AFAIK, seems to be WPA. WEP or unsecured are not desirable.

I, too would like be directed to a link to report this bug, or add this info if a bug  regarding the RaLink has been already posted.

---

### Post by xc3RnbFO8P on 2010-03-31
I had similar problem, had to set the >wireless >security encryption to **AES**.

---

### Post by eltonw on 2010-03-31
> **Ringi said:**
> I had similar problem, had to set the >wireless >security encryption to **AES**.
er, dummy instructions, please? Once you boot the live CD the network applet only provides me with  WPA/WPA2 personal as the encryption choice.
FWIW: I am connected to the same network with my Apple Powerbook (on which I am writing this post)

I have downloaded the Easy Peasy 1.6 beta (which is ubuntu-based, anyway) ... and *bingo*!
**Same problem**. Sad, sad, sad.....:sad::sad::sad::sad::sad:. (Please don't tell me I have to install the Windows OS that came with the Asus netbook or choose Windows 7:frown:)

---

### Post by xc3RnbFO8P on 2010-04-01
I'm talking about chancing the settings in the router( I'm using Linksys).
Open Firefox, type 192.168.1.1(Linksys) or 192.168.0.1(Level One) in the address bar
go to Wireless> Wireless Security> Security Mode= WPA2 Personal, Security Encryption, in my router I can
choose between (TKIP/AES) and (**AES**).

---

### Post by freakazo on 2010-04-01
My routers settings was already on AES, which ofcourse didn't work.
Setting it to AES+TKIP and just TKIP didn't work either.

Ps. I'm using a belkin usb wireless stick.

---

### Post by eltonw on 2010-04-01
> **Ringi said:**
> I'm talking about chancing the settings in the router( I'm using Linksys).
Open Firefox, type 192.168.1.1(Linksys) or 192.168.0.1(Level One) in the address bar
go to Wireless> Wireless Security> Security Mode= WPA2 Personal, Security Encryption, in my router I can
choose between (TKIP/AES) and (**AES**).
I also have a **Linksys** [Wireless-N Home Router **WRT120N-CA**]. 

But what about if I go out to an internet cafe such as one of those on the ISF (ilesansfil.org) network? Here at home, the Asus EEE 1000 PC netbook and my Apple Powerbook are on my network. 

Your suggestion also makes me think:-k of a recent connection problem here. I had a friend visiting with her Windows laptop, and she had a problem with MS Windows** _not being able to connect_ ... it kept *trying*, and *trying*... fortunately, I have a D-Link DWL-122 USB adapter, with which she was able to connect. 

[I DO NOT USE Windows or any Microsoft products]

This still points to how important being able to connect is now of PRIMARY importance, since help, either via forums or live, AND updates are all done via Internet connection.

[FONT=Trebuchet MS][SIZE=2]I have  now downloaded and tested *THREE* deb based distros [*BETAS*]: Ubuntu Lucid, Easy Peasy 1.6, and EEEbuntu 4. :-(The problem is CONSISTENT with all three distros.
[/SIZE][/FONT]
Currently _[COLOR=DarkRed]**with Karmic**[/COLOR]_, it takes  _[COLOR=DarkRed]a few seconds, and my netbook is connected[/COLOR]_. Of course, _Snow Leopard_ [Mac OS/X 10.6.3] _connects immediately..._ so I think it would / might be fair to say that something is seriously broken in these betas.:frown:

Wishful thinking on my part,:-\":-\":-\" but I am 'dreaming of the day' when both my machines are / may be pure linux-run. (But then... I have an iPhone 3GS, so I'm stuck with Apple.)

---

### Post by xc3RnbFO8P on 2010-04-01
I got WRT 160N V2
In Wireless> Basic Wireless Settings> 
Wireless Configuration: Manual
Network Mode: Mixed
Radio Band: Auto
Wide Channel: Auto
Standard Channel: Auto

---

### Post by freakazo on 2010-04-02
Did anyone test this issue with one of the daily builds?
I'm bandwidth impaired so I can't just download a build that *might* not work.

---

### Post by absolut1983 on 2010-04-02
Same same here, but with a different card (an Atheros one that worked fine with Intrepid, Jaunty and Karmic).

   The funny thing is: I've just installed Mint Helena on the same laptop in order to get some work done and the problem seems to persist. I did manage to connect to me place's wireless network, but the speed is appalling.

   Mint Helena on a much older laptop (from which I'm posting this now) is working like a charm.

---

### Post by eltonw on 2010-04-02
> **Ringi said:**
> I got WRT 160N V2
In Wireless> Basic Wireless Settings> 
Wireless Configuration: Manual
Network Mode: Mixed
Radio Band: Auto
Wide Channel: Auto
Standard Channel: Auto
On the **Linksys WRT120N-CA** there is no "Radio Band" option. In place of that the option there is "Channel width" which I changed from **20 MHz** to **Auto** (20 MHz or 40 MHz) *Going by your directions above*, my other setting are the same (Auto).

... once again, I booted and tested all three deb-based betas: Lucid, Easy Peasy, and EEEbuntu. [FONT=Arial Black]Result: [COLOR=Red]still does not connect[/COLOR].[/FONT]:???:#-o:-# I see the indicator spinner / icon flashing, then the dialog popup shows [FONT=Arial Black][COLOR=Red]AGAIN asking for the WPA/WPA2 password[/COLOR][/FONT].#-o

FWIW: The router settings are at a _default security setting: (TKIP/AES) and (AES). _

[FONT=Comic Sans MS][COLOR=Sienna]Regardless of the settings, (and by comparison) my Powerbook connects **immediately**.[/COLOR][/FONT]

I would make bold to say that the problem is not with the router, but with the **RaLInk RT2860** network card in my Asus netbook... as the problem is consistent with three 'flavours' of debian.

Could you point me to a daily build of Lucid so I can test and see ***if*** it "plays better" with the RaLink?

TIA

---

### Post by xc3RnbFO8P on 2010-04-02
Read this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/442178]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/442178")

---

### Post by freakazo on 2010-04-03
> **eltonw said:**
> 

Could you point me to a daily build of Lucid so I can test and see ***if*** it "plays better" with the RaLink?

TIA

Yip, [here you go]("http://cdimage.ubuntu.com/daily-live/current/")

---

### Post by eltonw on 2010-04-05
> **freakazo said:**
> Yip, [here you go]("http://cdimage.ubuntu.com/daily-live/current/")
Thanks. Pardon my ignornce, but I guess the desktop build would be a bit 'heavier' [resources, packages] than the NBR? Also, is there any possiblity of a Beta *2* of Lucid?

---

### Post by eltonw on 2010-04-07
Well, that was a HUGE WASTE OF TIME.:-& 

I spent several days mucking about with my router, to the point that I even corrupted the connections in my Macbook.:frown: I had to get a friend to come over with his Windows laptop to correct everything, then I did a fresh install of OSX.

I've downloaded the nightly builds of the DESKTOP LUCID beta, lost a few CD's.  I have a 'functioning' desktop CD which did boot on the Macbook, but the CPU was too fast for me to use the Trackpad. I now have the same desktop CD booted on the Asus, but AGAIN, [FONT="Arial Black"][COLOR="Red"]I still cannot connect[/COLOR][/FONT][-([-( . I'm back to the consistent problem of the Ralink asking for the password over [pause], and over [pause], and over ... ad nauseam.

Once I boot back to KARMIC on the netbook's HD, I connect practically immediately.

[COLOR="Navy"]**On this SAME Asus EEE machine I've run several releases of ubuntu (8.04 through 9.10 ...the currently installed one). _There was never any need of special or third party drivers.**[/COLOR]_

**[FONT="Comic Sans MS"][COLOR="Purple"]Now** the RaLink is proving to be such a royal headache?[/COLOR][/FONT]:confused:

The connectivity issue still persists with the current beta (neither the NBR nor the Desktop versions work).

Again, I ask: is there / will there be a BETA 2 of Lucid?

---

### Post by cariboo on 2010-04-07
The release schedule is [here]("http://ubuntuforums.org/showthread.php?t=1304172"), the last stickie at the top of the page.

---

### Post by stoneguy on 2010-04-07
There've been some networking regressions between 9.10 and 10.04 testing. These show up on the 10" ASUS netbooks. Reports have been made on Launchpad, and we'll see whether Canonical has got things sorted out for beta2. If not and they final release without ASUS netbook support, that'll be a real hit to their credibility.

---

### Post by mikegu on 2010-04-07
I had the same problem with a Toshiba Satelite l305d ... i punted on the first try and went to Kubuntu, where i was able to connect wireless without a problem.  Decided to try again, and found solution (at least for me).  I have a Dlink 615 draft N router.  Had it set to dual-mode WPA/WPA2 - AES initially.  Tried setting to WPA2 - AES, no change - still failed.  Change to WPA - TKIP, connected without a problem.  Changed back to WPA2 - TKIP, connected without a problem.  Set it to WPA2, dual-mode TKIP/AES, connected without a problem.  Finally, switched back to WPA/WPA2 - AES ... this time it worked!  Final test was WPA2 - AES, and, wouldn't you know, it's still working.

What's wrong here ... this is the type of behavior I expect from that other OS!  I'm going to reboot my live CD and see if I continue to connect.

---

### Post by scokem on 2010-04-08
> **mikegu said:**
> I had the same problem with a Toshiba Satelite l305d ... i punted on the first try and went to Kubuntu, where i was able to connect wireless without a problem.  Decided to try again, and found solution (at least for me).  I have a Dlink 615 draft N router.  Had it set to dual-mode WPA/WPA2 - AES initially.  Tried setting to WPA2 - AES, no change - still failed.  Change to WPA - TKIP, connected without a problem.  Changed back to WPA2 - TKIP, connected without a problem.  Set it to WPA2, dual-mode TKIP/AES, connected without a problem.  Finally, switched back to WPA/WPA2 - AES ... this time it worked!  Final test was WPA2 - AES, and, wouldn't you know, it's still working.


I've noticed screwy behaviour from my laptop since I fully updated it yesterday.  I'd left my home connection (WPA2) in the saved networks list and after rebooting it failed to connect (continuously asked for the key again despite it being correct) so I deleted the entry from the network manager screen then attempted to reconnect - it worked first time.  Rebooted and it failed to connect again so I repeated the steps and it worked...

It's good that I can at least get a permanent connection now but rather annoying that it can't do it automatically.  It's almost like it's not saving something correctly or something seeing as the saved connection can't work.

---

### Post by seafury on 2010-04-08
Hi 

I had similar problem trying to connect to wifi.

What i did was the following.

After selecting your wireless name and it asks for password /key  it is say xx xx xx xx xx xx (upper and lower case and combination of munber and letters)

I initially inserted the whole key (no luck)
then i systematically dropped the last two digits. and tried again. Dropping the last 4 digits. try again.

Then it connected unfrotunately i cant remember how many digits it took It may be the first 6 or 8.


Same thing on my Win 7 machine not using the whole key.

Hope it helps.


Other than that Ubuntu 10.04 beta on AAO 531H is awesome. :-)

---

### Post by eltonw on 2010-04-10
> **stoneguy said:**
> There've been some networking regressions between 9.10 and 10.04 testing. These show up on the 10" ASUS netbooks. Reports have been made on Launchpad, and we'll see whether Canonical has got things sorted out for beta2. If not and they final release without ASUS netbook support, that'll be a real hit to their credibility.

[FONT="Arial Black"]_THANK YOU_ for this enlightenment![/FONT]

I always tend to give the "benefit of the doubt" to the 'other person'. I wasted a lot of time fiddling around for nothing.](*,) Let me [FONT="Arial Black"]emphasise[/FONT]: I have used at least three previous releases of ubuntu (and currently have Karmic NBR installed). Connection occurs almost instantly. :-x[FONT="Arial Black"]LUCID is the only version that is now causing so much trouble.[/FONT]:x

:arrow:[COLOR="Red"]Nowadays, ability to connect is [COLOR="DarkRed"]**primordial**[/COLOR] in running *any* computer system.[/COLOR] No matter what the problem, as long as you can log in to the system, and connect you can find help and / or a solution to a problem.

I trust that **canonical** / **ubuntu** will treat this with due urgency. Neither the NBR or daily desktop build  of LUCID will allow me to connect on my Asus EEE 1000 PC. so I won't bother to try beta 1. Since the proposed release of the gamma code is so near,[FONT="Verdana"] I hope that beta 2 comes out soon, *[COLOR="Red"]with the connectivity issues resolved.[/COLOR]*[/FONT]

"networking regressions" is putting it very mildly!:-#

---

### Post by WishMaster on 2010-04-10
I confirm this too:
RaLink RT 2800 802.11n PCI card
I see all available networks, network manager will not accept passphrase to connect.

---

### Post by eltonw on 2010-04-10
I have downloaded and successfully burned the Beta 2 NBR [ubuntu-10.04-beta2-netbook-i386.iso] on my MacBook, (in OSX 1.6.3) using a DVD-R (... if the medium matters...). Placed the disk in my external Samsung DVD/R drive and booted. Once the l**[SIZE="2"]ucid beta 2[/SIZE]** is booted as a live CD, I **[COLOR="Red"]try to connect[/COLOR] to** my Wifi **network**, and **[COLOR="Red"]NO LUCK[/COLOR]**.:frown:

 ](*,)[FONT="Verdana"][SIZE="3"]Same problem as discussed here:[/SIZE][/FONT]
[http://ubuntuforums.org/showthread.php?t=1438175]("http://ubuntuforums.org/showthread.php?t=1438175")

As with beta 1, it shows connected (I think, since it offers a choice to "disconnect"). The icon animation on the taskbar keeps churning and churning, then *BINGO*!!! ... the dialog pops up and asks for the password AGAIN. ... and again ... and again.... 

I purposely selected "_show password_" to ensure that I am indeed entering my PWD correctly.


**[SIZE="2"]What now?[/SIZE]**:???:

:-kIf I reboot from the live CD and back to Karmic on my netbook, I have NO PROBLEM to connect.

---

### Post by 23meg on 2010-04-10
If it's the same problem, why are you starting a new thread? Please continue in the existing one; merged.

---

### Post by jbcfarina on 2010-04-10
One more afraid of Lucid connectivity,...:(

---

### Post by PhilGil on 2010-04-10
An EEE PC 1000h user here, and I'm suffering from the same problem with my wireless.  As others have reported, wireless works flawlessly in 9.10 NBR.  I was hoping this would be resolved by Beta 2, but no luck so far.  I've been tracking this bug report in launchpad, which I believe is different than the one posted earlier in this thread: [https://bugs.launchpad.net/bugs/496093](https://bugs.launchpad.net/bugs/496093) .

Hope this is fixed soon.  I've played around with Lucid NBR and there are some very nice enhancements over Karmic, but until the wireless is fixed I won't upgrade.

---

### Post by ronacc on 2010-04-10
the regression in wireless does not just affect net books . My desktop since beta 1 will not connect  wireless on a first boot from off but connects normally on a reboot.

---

### Post by jbcfarina on 2010-04-10
I use a Desktop with rt2860 driver. I could connect in the live-Cd setting my router to use only wpa2-psk not mix (wpa and wap2 mixed) I hope this helps, but I am a little upset.with this regressions in drivers.

I have seen this work around[ ]("http://bbs.archlinux.org/viewtopic.php?pid=673730")[here]("http://bbs.archlinux.org/viewtopic.php?pid=673730").

---

### Post by josephellengar on 2010-04-10
I just upgraded my 1005ha-p eeepc from 9.10 to 10.04.  My wireless radio will not even turn on.  Whenever I try to turn it on I get the message "Could not enable WIFI radio"  I have tried various drivers and everything.  This broke day of the upgrade.

---

### Post by freakazo on 2010-04-13
F50D8053 v3

Tried this wireless usb stick aswell. Still the same problem with beta 1 and 2.

---

### Post by null_pointer_us on 2010-04-13
Ralink RT2860 drivers bundled with many releases of Ubuntu have had some horrible auto-detection bugs.

Depending on what combination of encryption types your router reports, the ralink drivers may fail to connect even when some of those encryption types are supported.

Similar bugs exist with wireless radio types (N, N+G, etc.).

The solution is to write a RT2860STA.dat file to force the driver to use settings compatible with your router.

EDIT: I've attached the official RT2860STA.dat manual and a little how-to I wrote for myself about where to place the RT2860STA.dat and how to make sure the driver accepts it.

---

### Post by eltonw on 2010-04-13
> **null_pointer_us said:**
> Ralink RT2860 drivers bundled with many releases of Ubuntu have had some horrible auto-detection bugs.

Depending on what combination of encryption types your router reports, the ralink drivers may fail to connect even when some of those encryption types are supported.

Similar bugs exist with wireless radio types (N, N+G, etc.).

The solution is to write a RT2860STA.dat file to force the driver to use settings compatible with your router.

EDIT: I've attached the official RT2860STA.dat manual and a little how-to I wrote for myself about where to place the RT2860STA.dat and how to make sure the driver accepts it.

**Three questions:**

1) Does this mean that if running ubuntu as a live CD, the user has to write the driver (as described above) BEFORE he can connect?

2) What about those of us who are not sufficiently skilled in networking ...are we "doomed"?:(

3) The present drivers DO work. I have no problems connecting here at home ***or*** at a public hotspot. 

:confused:*[SIZE="2"]Why[/SIZE]* can't the current drivers be used in the upcoming gamma of LUCID?:confused: 

[COLOR="Sienna"]_I reiterate:_ three or four _previous releases of ubuntu_ _on the **same netbook** never presented this problem_, and the current (Karmic) also connects me without problems.[/COLOR]

**[CENTER]Changing the current working drivers is not very "LUCID", IMVHO![/CENTER]**

[FONT="Comic Sans MS"]/Wondering aloud: did Asus *purposely* design its netbooks with the Ralink cards knowing this incompatibility linux, just to 'chase' users (back) to Windows? ... speculate on a 'conspiracy' methinks?[/FONT]

---

### Post by null_pointer_us on 2010-04-13
**Three answers:**

1) No, it means he/she has to write a 5-6 line config file (RT2860STA.dat) as I described.

2) You can find most of these settings in your router's config.

3) Yes, the drivers do work if you *happen* just the right setup at a given location. If not, create the text file.

> :confused:*[SIZE="2"]Why[/SIZE]* can't the current drivers be used in the upcoming gamma of LUCID?:confused:

:confused:*[SIZE="2"]Where[/SIZE]* did you get the idea that you needed a new DRIVER?:confused:

> [COLOR="Sienna"]_I reiterate:_ three or four _previous releases of ubuntu_ _on the **same netbook** never presented this problem_, and the current (Karmic) also connects me without problems.[/COLOR]

[COLOR="Sienna"]_I've solved_ the same problem in three or four _previous releases of Ubuntu_ _on the **same PC**_. This problem is most certainly present in Karmic.[/COLOR]

In addition to the type of problems I described how to fix, there's also the possibility of new bugs, but you seem too busy throwing a fit (?) to determine the exact cause of your problems.

> **[CENTER]Changing the current working drivers is not very "LUCID", IMVHO![/CENTER]**

[CENTER]**I agree!**[/CENTER]

> [FONT="Comic Sans MS"]/Wondering aloud: did Asus *purposely* design its netbooks with the Ralink cards knowing this incompatibility linux, just to 'chase' users (back) to Windows? ... speculate on a 'conspiracy' methinks?[/FONT]

[FONT="Comic Sans MS"]/Wondering aloud: did eltonw *purposely* misread my comment knowing this problem, just to 'confuse' the issue? ... speculate on a 'conspiracy' methinks?[/FONT]

Seriously, it's been buggy like this for many releases.

When Canonical (or Ralink) fixes the existing driver, then the situation will improve.

---

### Post by josephellengar on 2010-04-13
> **null_pointer_us said:**
> **Three answers:**

1) No, it means he/she has to write a 5-6 line config file (RT2860STA.dat) as I described.

2) You can find most of these settings in your router's config.

3) Yes, the drivers do work if you *happen* just the right setup at a given location. If not, create the text file.



:confused:*[SIZE="2"]Where[/SIZE]* did you get the idea that you needed a new DRIVER?:confused:



[COLOR="Sienna"]_I've solved_ the same problem in three or four _previous releases of Ubuntu_ _on the **same PC**_. This problem is most certainly present in Karmic.[/COLOR]

In addition to the type of problems I described how to fix, there's also the possibility of new bugs, but you seem too busy throwing a fit (?) to determine the exact cause of your problems.



[CENTER]**I agree!**[/CENTER]



[FONT="Comic Sans MS"]/Wondering aloud: did eltonw *purposely* misread my comment knowing this problem, just to 'confuse' the issue? ... speculate on a 'conspiracy' methinks?[/FONT]

Seriously, it's been buggy like this for many releases.

When Canonical (or Ralink) fixes the existing driver, then the situation will improve.

I never had the problem with karmic.  Actually, due to this problem, I just wiped my netbook and installed karmic.  Wireless was working out of the box.  Unless the devs fixed that already ...

---

### Post by eltonw on 2010-04-14
> **rossholley said:**
> I never had the problem with karmic.  Actually, due to this problem, I just wiped my netbook and installed karmic.  Wireless was working out of the box.  Unless the devs fixed that already ...

The previous three or four releases of ubuntu were clean installs on the same Ausus machine, different routers, and more recently) a different location / ISP. 

I did not try the LUDID Alpha since I am not prepared to takes the risks that level of code entails.

[FONT="Comic Sans MS"][COLOR="DarkOliveGreen"]BOTH Lucid Beta 1, and Beta 2 (NBR / and / or Desktop) consistently fail to connect when booted as a "LIVE CD".
[/COLOR][/FONT]


... [COLOR="Red"]to clarify[/COLOR]: as for my 'soliloquy' about 'conspiracy' it was **not**[-X_ directed at either Ubuntu or Canonica_l... it was _[COLOR="Olive"][SIZE="3"]intended as sarcasm at :twisted: **ASUS[/COLOR]_** who have now officially dumped LINUX / Open Source [/SIZE]:frown:

I do not use Windows, and any manufacturer who insists on supporting ONLY Windows does not / no longer will get my business.

---

### Post by eltonw on 2010-04-15
@ rossholley:
Today I had a look at launchpad, and WRT UBUNTU and RALINK (non-compatiblity?)  in general,***this*** is what I found:
[https://launchpad.net/+search?field.text=ralink](https://launchpad.net/+search?field.text=ralink)
:(

---

### Post by eltonw on 2010-04-15
ADDENDUM:
Posted additional comments in Launchpad:
[https://bugs.launchpad.net/linux/+bug/496093]("https://bugs.launchpad.net/linux/+bug/496093")

**NOTA BENE:**
_*Duplicates* of this bug_
Bug #497320
Bug #524867
Bug #529097
Bug #543816
Bug #549027

It looks like the main culprit is here:
linux-kernel-bugs #14750

Sol this even affects some RPM-based distros.

Perhaps by the time LUCID becomes gamma an updated kernel will be in the release.

respectfully,

---

### Post by eltonw on 2010-04-16
UPDATE:
One of my correspondents in Russia pointed me HERE:
[http://www.ralinktech.com/support.php?s=2]("http://www.ralinktech.com/support.php?s=2")

**[SIZE="2"][FONT="Verdana"][COLOR="DarkGreen"]It would be nice *if*[/COLOR][/FONT][/SIZE]** these [COLOR="DarkGreen"][FONT="Verdana"][SIZE="2"]drivers could be incorporated[/SIZE][/FONT][/COLOR] into the kernel, [COLOR="DarkGreen"][FONT="Verdana"][SIZE="2"]or[/SIZE][/FONT][/COLOR] _[COLOR="DarkRed"]at the very least[/COLOR]_, [COLOR="DarkGreen"][SIZE="2"][FONT="Verdana"]included on the CD[/FONT][/SIZE][/COLOR]. 
If not ... [FONT="Arial Black"]IMVHO[/FONT] ...it would defeat the purpose to " boot as LIVE CD" or install LUCID LYNX, only to be told "_download the drivers" when you cannot even connect to do so_!:lolflag:

---

### Post by DidRocks on 2010-04-18
I really think that anyone having this issue should report a bug if they really want it to be fixed. Developers rarely reads forums as there are already a huge amount of bugs ([https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs))


PS: sorry, only saw the first page (bad cache in my proxy), saw that it was already done ^^

---

