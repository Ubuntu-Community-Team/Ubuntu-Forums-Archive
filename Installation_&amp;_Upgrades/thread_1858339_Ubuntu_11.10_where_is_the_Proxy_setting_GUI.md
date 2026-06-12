---
title: "Ubuntu 11.10: where is the Proxy setting GUI?"
date: 2011-10-12
forum: Installation &amp; Upgrades
---

### Post by samuele.pretini on 2011-10-12
Hi at all,

yesterday I have installed the 11.10 Ubuntu version. It is great for me, but today when I come at work, I haven't found the proxy setting application gui.

If I open the dash and digit "proxy", it is doesn't appear.

How can I set my proxy now?

Thanks.

Samuele

---

### Post by kaimi&#326;iece on 2011-10-13
I had the same problem and figured out you have to search for "network" instead of "proxy" now. At least the new proxy manager doesn't prompt for the password twice.

---

### Post by kaimi&#326;iece on 2011-10-13
Turns out the new proxy manager doesn't have a "use the same proxy for all protocols" option, so I now get errors like this: "Error in proxy URL [https://x.x.x.x:8080/:](https://x.x.x.x:8080/:) Must be HTTP." Fail!

---

### Post by FrancoisQueinnec on 2011-10-14
Well.. I've tried setting the proxy there, but didn't work :(

Basically, I entered my proxy settings on all 4, Apply systemwide, entered my password... 
It's been saved, as when I re open that proxy configuration window, it's there.. but so far, the system and chromium can't access the internet..
On firefox, I've configured it not to use the system proxy, and entered the same configuration, and it does work !

So, basically.. system proxy doesn't seem to work at all :(

I miss the old proxy window (especially with the possibility to name and save proxy settings ).

I wonder, is it so uncommon to have a laptop that often has to change proxy settings (home / office) ???????

---

### Post by Skunkzz on 2011-10-14
> **FrancoisQueinnec said:**
> 

Basically, I entered my proxy settings on all 4, Apply systemwide, entered my password... 
It's been saved, as when I re open that proxy configuration window, it's there.. but so far, the system and chromium can't access the internet..
On firefox, I've configured it not to use the system proxy, and entered the same configuration, and it does work !



Same exactly problem here.... if anyone has any leads on how to configure proxy, please help us

---

### Post by bemanuel.pe on 2011-10-14
> **Skunkzz said:**
> Same exactly problem here.... if anyone has any leads on how to configure proxy, please help us

For now install gnome-shell

---

### Post by Sollmeeya on 2011-10-15
I am having the same problem, can you explain a little more about gnome shell?

---

### Post by xenodevil. on 2011-10-17
i'm having the same problem! can't use internet at office now besides for normal browsing :S to add confusion to this, the window which appears in firefox for proxy's username and password has the 'Cancel' as default button, so you can't just type and press enter! :@ had to enter password about 10 times to figure it out! thats a DOUBLE fail!

i found a few CLI settings but apparently they work only for the CLI scripts, but again these settings aren't working even with apt or wget for me.. :S
checked the ubuntu clssic at home last night, its all messed up too.. i think this is because i upgraded from 11.04 (happened when i upgraded from 10.10 to 11.04 too and at that time i had to do a clean install to fix it) but let me see if the settings are still present there..

i really hope this gets fixed in unity soon enough.. :S

---

### Post by xenodevil. on 2011-10-17
omg! just found out the setting.. you have to go to search for Network and then go to the "Network" in the results (NOT Network Connections). The icon for it is just like the "Browse Network" link for browsing your network and thats why i kept missing it! The setting is present there and working for me. Phewww.. :D

You can also find this setting by clicking on the System Settings on the Shutdown menu and choosing Network..

---

### Post by FrancoisQueinnec on 2011-10-17
Reverted to 11.04 .. way too many problems with 11.10 :(

---

### Post by summojc on 2011-10-17
use the ubuntu-button in the left-top corner, write network, click network and you will see the settings for proxy :p
You'll have a problem with firefox! It doesn't work for firefox, so set the proxy-configuration for firefox manual. that's it!

---

### Post by FrancoisQueinnec on 2011-10-17
yeah.. problem is .. it still didn't work !

---

### Post by mfaroukg on 2011-10-17
> **FrancoisQueinnec said:**
> Reverted to 11.04 .. way too many problems with 11.10 :(

too bad for me, i can't do the proxy as it was in 11.04, but i can't go back because it is big headache.

I am using the network in the photo attached. it helps for few but not comfortable.

---

### Post by Marconian on 2011-10-17
It's impossible to set up proxy authentication in this window. Even though I use the way username:password@host in the address field it doesn't work. It also doesn't have a button to use the same proxy to all protocols. It's strange because in 11.04 all this worked just fine and now they removed the working functions!

---

### Post by m@ssimilianonball on 2011-10-17
Same problem here: system proxy won't work. But i've tried with the firefox proxy settings and it works perfectly! :)

The only problem whit this kind of configuration is that the only application that work trhrough the proxy is firefox, all the others are offline :(

---

### Post by silvavlis on 2011-10-18
I don't really get why Canonical is trying so hard to get rid of users with non-standard configurations and power users... ](*,)

How do they come to the idea of releasing a product with less features!! Yeah, nicer, but I cannot waste my time this way... [-X

---

### Post by FrancoisQueinnec on 2011-10-20
honnestly, I don't even understand why they keep those proxy settings as 'global' instead of 'per network'... 

I mean, we have different proxy settings whether we're using the home network or the office / whatever network... Common sense would say to automatically switch proxy settings according to the network we're connected to.. but no... not for Canonical !

---

### Post by jsinca on 2011-10-20
Ignore the proxy GUI page.

type this in a terminal

sudo gedit /etc/apt/apt.conf.d/02proxy

add this

```
Acquire::http::Proxy "http://address:port/";
Acquire::ftp::Proxy "ftp://address:port/";

```

If you require authentication then

```
Acquire::http::Proxy "http://username:password@address:port/";
Acquire::ftp::Proxy "ftp://username:password@address:port/";

```

---

### Post by weixing on 2011-11-06
> **jsinca said:**
> Ignore the proxy GUI page.

type this in a terminal

sudo gedit /etc/apt/apt.conf.d/02proxy

add this

```
Acquire::http::Proxy "http://address:port/";
Acquire::ftp::Proxy "ftp://address:port/";

```

If you require authentication then

```
Acquire::http::Proxy "http://username:password@address:port/";
Acquire::ftp::Proxy "ftp://username:password@address:port/";

```
I had same problem, too
thanks to you, it's ok now...

---

### Post by mr.interested on 2011-11-08
> **jsinca said:**
> sudo gedit /etc/apt/apt.conf.d/02proxy

```
Acquire::http::Proxy "http://username:password@address:port/";
Acquire::ftp::Proxy "ftp://username:password@address:port/";

```

Unfortunately, that didn't work for me. After creating a file '02proxy' (as it didn't exist) and typing

```
Acquire::http::Proxy "http://myusername:mypassword@proxy.address.com:8080/";
Acquire::ftp::Proxy "ftp://myusername:mypassword@proxy.address.com:8080/";

```

the proxy isn't recognized, even after restarting the system. Is there anything else I should do?

I'm 100% sure that the address and login details are correct, as I even copied and pasted them to, for example, Dropbox settings (which works).

---

### Post by Ben-G89 on 2011-11-08
Hey I got the same problem.

But jsincas advise helped me.

> **jsinca said:**
> Ignore the proxy GUI page.

type this in a terminal

sudo gedit /etc/apt/apt.conf.d/02proxy

add this

```
Acquire::http::Proxy "http://address:port/";
Acquire::ftp::Proxy "ftp://address:port/";

```

If you require authentication then

```
Acquire::http::Proxy "http://username:password@address:port/";
Acquire::ftp::Proxy "ftp://username:password@address:port/";

```

But I don't really understand what the gui network proxy setting is doing. Maybe this get fixed the next release. I will wait :popcorn:

---

### Post by mr.interested on 2011-11-08
> **Ben-G89 said:**
> Hey I got the same problem.

But jsincas advise helped me.

Did you use authentication? I need one, and the posted solution doesn't work for me unfortunately.

---

### Post by bjornsol on 2011-11-11
My problem is that the proxy setting works for everything else except the browser - i.e. for Synaptic, update etc. For Firefox I still have to set and unset manually. For 11.04 and earlier release, I could set the proxy in the GUI and I could set the Firefox setting to "Use system default" and then I'd only need to change the proxy in one place. Now I have to do it both in Firefox *and* in the GUI. Fail.

---

### Post by adriaan_botha on 2011-11-16
Ubuntu can't get this right, it has never properly worked from previous versions, now it is just plain right confusing.

Have they forgotten the asking password dialog box, and actually saving this correctly. Also I bet you something with a $ in the password will not work, since it needs to be %24.

I am red faced inside the office, this release seems so nice, but once again the proxy problem, working at home great, love it, coming to work, it suck, now i have to work on my Win 7 pc, sighhhhh:(

---

### Post by zcats on 2011-11-18
Hi
I have same problem Ubuntu 11.10 with proxy setting to "none" using GUI. However, I was earlier on corporate network and seems to have set apt-get to use proxy. Strange that all GUI apps that need the net work: ie synaptic works, browser works but apt-get doesnt...! Errors are failed to connect to my work proxy. The setting is in apt.conf is empty!  How do I set to "no proxy?"..maybe use localhost as address, but what for the port?
We need a simple way to set proxy and auto change for different networks: such as moving from corporate to home.
Maybe I try Wiicd?

---

### Post by Rudi VanDiSarzio on 2011-11-18
Just got this working.
 
Connecting to MS Forefront Proxy device so required AD authentication, with 11.10 running as a guest on VM Player on Windows 7 64-bit Enterprise.  AD connected PC, with functioning connection to proxy.
 
Using System Settings - Network - Network Proxy.
 
Method - Manual
 
HTTP Proxy - domain\username:password@Proxy IP address
Repeat for all other entries
 
Apply system wide.
 
This did not work first time, rebooted and the Ubuntu Update service burst into life - kerching!  Firefox working as well.

---

### Post by jitesh_0149 on 2011-11-22
To set proxy in Ubuntu 11.10, you just need to set proxy in "**Network**" which will be available after searching network in dash board menu..

Then install **dconf-tools** by using command in terminal,

sudo apt-get install dconf-tools

After this type dconf-editor or it can also be found in search of dash board menu

write dconf-editor and go to **system->proxy** in menu available at left side and click on proxy and configure hosts that you want to ignore proxy..

Also click on http menu under proxy and check the checkbox shown as enable...

After this just disconnect and connect your network, hope this will work...:p

---

### Post by mr.interested on 2011-11-26
> **jitesh_0149 said:**
> To set proxy in Ubuntu 11.10, you just need to set proxy in "**Network**" which will be available after searching network in dash board menu..

Then install **dconf-tools** by using command in terminal,

sudo apt-get install dconf-tools

After this type dconf-editor or it can also be found in search of dash board menu

write dconf-editor and go to **system->proxy** in menu available at left side and click on proxy and configure hosts that you want to ignore proxy..

Also click on http menu under proxy and check the checkbox shown as enable...

After this just disconnect and connect your network, hope this will work...:p

Many thanks for your advice. Unfortunately, it doesn't work :(

STEP 1

I've set up the proxy on 'Network' manager and applied system wide (the last attachment).

STEP 2

I've configured proxy through dconf-editor (the first three attachments).

STEP 3

I've reconnected and restarted Ubuntu a few times. Unfortunately, it doesn't work.

Any suggestions?

---

### Post by mr.interested on 2011-11-28
Any ideas? It's very frustrating to manually change proxy settings twice a day for every application I use... :(

---

### Post by mr.interested on 2011-11-29
To just update, interestingly, the things that work are:
a) 'lookup' function in the 'network tools', but anything else (eg, ping, whois), doesn't work.

b) Update Manager automatically detects updates and there's no problem to  install them. However, for some reason it doesn't ask me for password  (as it asks me when I'm not connected to the internet through proxy).

c) However, as per (b),
```
sudo apt-get update
```doesn't work properly. I'm getting many errors like this:
> W: Failed to fetch *** Proxy authentication requiredd) but... Ubuntu Software Centre works, I can install any software from there (and it does ask me for a password), and screenshots also work (they didn't work before setting up proxy).

d) Weather Indicator works, although the icon of weather disappears straight after 'refresh', and question mark appears. However, the weather conditions are correct, including forecast.

e) External software (Dropbox, Firefox) don't work when left with 'auto-detect' or 'system proxy settings' with a small exception: In Firefox, when 'auto-detect proxy settings for this network' is selected, page cannot be loaded. But with 'use system proxy settings', page loads forever, but it also never gets loaded.

f) On terminal, I can install any software, but I cannot use, for example, ssh, and I get:
> ssh: connect to host *** port 22: Connection refused

---

### Post by XTREEM|RAGE on 2011-12-20
Does anyone have a full working proxy with 11.10?

---

### Post by ebaker on 2012-03-30
Thank you - this worked perfect for me on Lubuntu 11.10!

> **jsinca said:**
> Ignore the proxy GUI page.

type this in a terminal

sudo gedit /etc/apt/apt.conf.d/02proxy

add this

```
Acquire::http::Proxy "http://address:port/";
Acquire::ftp::Proxy "ftp://address:port/";

```If you require authentication then

```
Acquire::http::Proxy "http://username:password@address:port/";
Acquire::ftp::Proxy "ftp://username:password@address:port/";

```

---

