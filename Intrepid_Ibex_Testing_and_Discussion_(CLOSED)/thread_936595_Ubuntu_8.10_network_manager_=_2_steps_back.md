---
title: "Ubuntu 8.10 network manager = 2 steps back?"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by blastzilla on 2008-10-02
I just completed a fresh install of ubuntu 8.10 to see how this side of the universe is coming along and I have to say, what are people thinking?  I thought editing rc.inet1.conf files was hard, using the GUI equivalent is even harder!

The LAN/Wired screen is interesting.  95% of desktop users need a simple screen with a couple of fields asking what the IP address should be, what the DNS server is and what the default gateway should be.  The remaining 5% need an additional screen to input additional IP addresses to connect to their developer networks, DMZ's etc etc.  The screens in this application are not for the home user and looks like it was designed for developers.

Wouldnt an IPv4 setting be more important than knowing what the 802.1x security setting was?  Do 95% of the users out there use 802.1x security on their wired networks?  Do 99% of users need to know what their network MTU or MAC address is for their LAN?  Wouldnt those “features” fall under an advanced configuration page - and then be entirely removed because it doesnt follow the Gnome UI standards.

The wireless program detects WLANs quite well. You click on the network that you want to connect to, it displays the right settings... except you cant save your password.  However, I see something that I've never seen before – show your password.  Wow, that is impressive!  Why cant that be a standard for the rest of gnome?  
Prompt: What is your wireless password?
Me: I'm not sure if I typed it in right... 
Prompt: Why dont I show you the password you entered, those asterixes can get annoying.
Me: Cool, can I also phone a friend and order a pizza?

Isnt that button on that screen supposed to read “Save your Password” and then save it?  I would have thought with an encrypted home folder, I would be able to store atleast some information in an encrypted state and allow programs I have running (document editor, spread sheet, network management program based on HAL and dbus) to read my data and preferences.

What is the use of having an encrypted home folder when I cant store information that will allow me to connect to my home network?

The only way I seem to be able to save my password is to click the right check boxes across a couple of screens in the correct order and then save it as the root user somewhere.  But does that mean that the password is now stored in plain text?  Should I be worried that I can boot the computer up in single user mode and read what the password should be?

Cant the developers look to other programs, such as the wireless program in microsoft vista.  I like my single click, enter password, click check box, then never worry about it again.  There is something comforting knowing that you have setup 1 thing properly and never having to look at it again.

Which takes me to the VPN screen.  I wanted to see if that screen would take OpenVPN settings as OpenVPN seems to be the way of the future.  I click on the networking icon near the time on the top right hand corner of the screen, see the option “VPN Connections”, then click “Configure VPN...” and see a screen that is completely greyed out.  Is that because it has not been written yet?  Wouldnt it be more impressive to have hidden the options and not give people hope that there was finally a way to configure VPN connections using a single GUI?

On the bright side, I'm impressed with the flashing orange progress bars.  They look magical.  Especially when they move for wireless networks that I'm not connected to.  Except for the live network that I'm connected to – that one doesnt move because it isnt working? Can that be fixed and maybe drawn in a different colour?  I would think a green moving progress bar for the network I'm connected to would be a mind blowing way to inform the user which network they're connected to and that it is working.  

Either way I'm not sure if this 'new' applet is a step forward or a step backwards for this release.  I cant understand how anyone will be able to use this program without feeling some level of frustration.  

As the core of ubuntu, I would suggest some work be done on this – as the old argument goes: we cant give you access to an nvidia driver for your PC because we cant modify it and make it better.  

Who can modify this application, make it compatible with the ethos of gnome and Ubuntu?

---

### Post by cariboo on 2008-10-03
You have to remember that the beta of Intrepid just came out today. Bugs are still being fixed as we speak, for instance you can now right click on your name in the top panel and log out to a guest user, that hasn't worked through all the alphas even though the option has been available since alpha2. Today after an update it finally worked. Ther will be a lot of improvements between now and the rc release on Oct 32rd.

Jim

---

### Post by wgrant on 2008-10-03
> **blastzilla said:**
> I just completed a fresh install of ubuntu 8.10 to see how this side of the universe is coming along and I have to say, what are people thinking?  I thought editing rc.inet1.conf files was hard, using the GUI equivalent is even harder!

The LAN/Wired screen is interesting.  95% of desktop users need a simple screen with a couple of fields asking what the IP address should be, what the DNS server is and what the default gateway should be.  The remaining 5% need an additional screen to input additional IP addresses to connect to their developer networks, DMZ's etc etc.  The screens in this application are not for the home user and looks like it was designed for developers.

Wouldnt an IPv4 setting be more important than knowing what the 802.1x security setting was?  Do 95% of the users out there use 802.1x security on their wired networks?  Do 99% of users need to know what their network MTU or MAC address is for their LAN?  Wouldnt those “features” fall under an advanced configuration page - and then be entirely removed because it doesnt follow the Gnome UI standards.


95% of desktop users don't need a screen at all - it will automatically connect using DHCP. Perhaps the tabs should be in the opposite order for the few users who will need more.

You also seem to be complaining about the presence of the advanced options, and then in the same sentence complaining that GNOME would remove them. Your contradictions confuse me.

> 
The wireless program detects WLANs quite well. You click on the network that you want to connect to, it displays the right settings... except you cant save your password.  However, I see something that I've never seen before – show your password.  Wow, that is impressive!  Why cant that be a standard for the rest of gnome?  
Prompt: What is your wireless password?
Me: I'm not sure if I typed it in right... 
Prompt: Why dont I show you the password you entered, those asterixes can get annoying.
Me: Cool, can I also phone a friend and order a pizza?

Isnt that button on that screen supposed to read “Save your Password” and then save it?  I would have thought with an encrypted home folder, I would be able to store atleast some information in an encrypted state and allow programs I have running (document editor, spread sheet, network management program based on HAL and dbus) to read my data and preferences.

What is the use of having an encrypted home folder when I cant store information that will allow me to connect to my home network?

The only way I seem to be able to save my password is to click the right check boxes across a couple of screens in the correct order and then save it as the root user somewhere.  But does that mean that the password is now stored in plain text?  Should I be worried that I can boot the computer up in single user mode and read what the password should be?


I believe that the per-user network key is stored in gnome-keyring - it is for me. Same as always. But if you save it as a system setting, it is (by necessity) stored as plaintext.

> 
Cant the developers look to other programs, such as the wireless program in microsoft vista.  I like my single click, enter password, click check box, then never worry about it again.  There is something comforting knowing that you have setup 1 thing properly and never having to look at it again.


How is that not how it works now? I just click on the network, enter my key, click "Connect". Notice that I'm connected. Reboot. Notice that I'm connected again.

> 
Which takes me to the VPN screen.  I wanted to see if that screen would take OpenVPN settings as OpenVPN seems to be the way of the future.  I click on the networking icon near the time on the top right hand corner of the screen, see the option “VPN Connections”, then click “Configure VPN...” and see a screen that is completely greyed out.  Is that because it has not been written yet?  Wouldnt it be more impressive to have hidden the options and not give people hope that there was finally a way to configure VPN connections using a single GUI?


There is. There was in Network Manager 0.6 too. You just need to install the appropriate network-manager-<somekindofvpn> package. OpenVPN, PPTP and Cisco (vpnc) VPNs are supported. Same as always.

> 
On the bright side, I'm impressed with the flashing orange progress bars.  They look magical.  Especially when they move for wireless networks that I'm not connected to.  Except for the live network that I'm connected to – that one doesnt move because it isnt working? Can that be fixed and maybe drawn in a different colour?  I would think a green moving progress bar for the network I'm connected to would be a mind blowing way to inform the user which network they're connected to and that it is working.  


That's the fault of the GTK theme, I believe.

> 
Either way I'm not sure if this 'new' applet is a step forward or a step backwards for this release.  I cant understand how anyone will be able to use this program without feeling some level of frustration.  


Most users will never need to enter the connection editor. Even if they do, it's certainly an awful lot better than NM0.6. There are more options (most of them hidden from view), it supports 3G, DSL, static IPv4 addresses, 802.1x wired authentication, and is generally a whole lot nicer. Please file any concrete issues that you can find with it as bugs on Launchpad.

> 
As the core of ubuntu, I would suggest some work be done on this – as the old argument goes: we cant give you access to an nvidia driver for your PC because we cant modify it and make it better.  

Who can modify this application, make it compatible with the ethos of gnome and Ubuntu?

I don't see much wrong with it now.

---

### Post by wilsong on 2008-10-03
I agree it has some issues, hopefully they will be ironed out..

---

### Post by wgrant on 2008-10-03
> **wilsong said:**
> I agree it has some issues, hopefully they will be ironed out..

We don't just magically identify and iron out issues. We need to know about them before we can do that. [File bugs]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+filebug")!

---

### Post by iponeverything on 2008-10-03
On the upside -- for me it works better. "Connection information" and Signal strength match what iwconfig report and it notices card removal instantly, instead of having a 10 second lag.

---

### Post by Bossieman on 2008-10-03
NM still says Connecting to GSM network when I connect to my HSPA/3G network, Good work there. No confusion at all :guitar: for the newbies.

NM doesn't have the option of HSPA/Turbo-3G anywhere at all. Still it is supposed to support it and I can use my E220 modem that only works with HSPA/Turbo-3G if I choose connect to GSM network. :popcorn:

---

### Post by jerome1232 on 2008-10-03
I'd have to say I love the new NM applet, I have noticed an issue that it won't save the password for me (if I get disconnected or reboot it will ask for my passphrase again)

edit: I see I have more updates, and I've read in other threads this has been fixed. Crossing fingers

---

### Post by nittanylion on 2008-10-03
? Ever since day 1, I've enjoyed the changes in nm, but I've always been able to save my password. And this was only after entering it on the one screen I was shown when it asked for the passphrase (using WPA, if it matters). One thing that's a huge step up for me is the lack of the keyring -- if I have to enter in my keyring pw every time I attempt to connect to my encrypted network, I might as well just re-enter the password to the network. 

Just might not be as bad as you think...

---

### Post by jerome1232 on 2008-10-03
Well after updates it's fixed, my password just wasn't making it to the keyring, now it does.

I've never had to enter a password to unlock the keyring, I've always had it set to just unlock when I logged in.

---

### Post by timcredible on 2008-10-03
if you find something wrong with 8.10, help out and file a bug so it can get fixed (if you download an alpha or beta version, that pretty much makes you a tester).

---

### Post by hamsandwich on 2008-10-15
In 8.04, the newtork-manager-openvpn (as well as the pptp plugin) had a checkbox for "direct all traffic through tunnel" or some such wording. That checkbox is now missing, and I'm not sure if all my traffic is or isn't going thru the tunnel - my preference would be no.

When I first used network-manager to handle VPN connections in 8.04, I was very impressed, because it worked smoother and with less configuration than windows. But now the GUI has changed and I am not sure of the rationale but unless I'm missing something it is a step backward. Am I supposed to enter a route to do this? The VPN route is added automatically...it would be some other setting in the .ovpn file...which I might be able to modify IF the 8.10 version imported or exported its settings. It does neither unfortunately.

---

### Post by Mr. Picklesworth on 2008-10-15
> **nittanylion said:**
> One thing that's a huge step up for me is the lack of the keyring -- if I have to enter in my keyring pw every time I attempt to connect to my encrypted network, I might as well just re-enter the password to the network. 

You should know that the keyring is indeed still there, and better than ever. If it was removed, that would be a *bad* thing since your password would no longer be encypted and stored automatically by a centralized tool (read: good security support).

The change you are noticing is that the keyring now unlocks automatically when you log in.

I must agree, the Edit Connections dialog is a user interface disaster, but it isn't fixable for this release. Hopefully it will see some tweaks in the future. At least the thing uses GTK, though, and is accessible.

On the bright side, I like "connect to hidden wireless network" on the main interface. It's a nice distinction.

---

### Post by linomac on 2008-10-16
the situation in kubuntu i think is even worse

---

### Post by stephantom on 2008-10-16
> **wgrant said:**
> You just need to install the appropriate network-manager-<somekindofvpn> package. OpenVPN, PPTP and Cisco (vpnc) VPNs are supported. Same as always.

I'm asking myself why there is no message or notice that allows me to comfortably install the right packages (just like codecs in totem or gtk-engines in gnome-appearance-properties).

---

