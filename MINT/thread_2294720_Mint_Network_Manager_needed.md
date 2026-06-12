---
title: "Mint Network Manager needed?"
date: 2015-09-12
forum: MINT
---

### Post by sentinel2 on 2015-09-12
I'm somewhat new to Linux, but not to firewalls. I've played around with different versions of Linux and Unix over the years but never seriously. Recently I decided to give it another try so, upon someones recommendation I installed Linux Mint Mate on a test machine. So far so good.

With someones help and tutelage I have been learning iptables and setting up a firewall rule set. I think I have a fairly good rule set installed and running now but every time I reboot I lose it obviously because it isn't saved in any boot time config file. Which brings me to my problem.

I have done some reading around and there are fairly easy to follow instructions on how to set your rule set to be run on boot but all of them seem to say that if you are running Network Manager then all best are off. They say that Network Manager conflicts with everything and to get your rule set to work in a config file with it running is iffy at best.

So my question is: Is this true? Would it be easier to config stuff if I get rid of Network Manager (which comes installed by default in Mint)? If so can I remove Network Manager without messing everything up? I have no problem getting rid of it if it's not necessary. I am fine with configuring my network manually if that's what I have to do. I'm sure I can find out here how to do that.

---

### Post by steeldriver on 2015-09-12
Hello and welcome to the forums

I've not heard anything about NetworkManager interfering with the ability to save and load iptables rules - do you have a link/reference for that?

---

### Post by Bucky Ball on 2015-09-13
*Thread moved to **MINT**.*

---

### Post by sentinel2 on 2015-09-13
Here is one page, but I've read it in others too.

[https://help.ubuntu.com/community/IptablesHowTo#Configuration_on_startup](https://help.ubuntu.com/community/IptablesHowTo#Configuration_on_startup)

Most pages say to edit a file that does not exist is Network Manager is installed. So I'm guessing that the presence of Network Manager causes a the same settings to be called from a file with a different name which adds a level of complexity that may not be necessary if one can live without Network Manager. I guess it depends on what it does for me that I would then have to do for myself if I uninstalled it. If all it does is a few simple things that I could do with editing a few simple files that I'm certainly willing to get rid of it.

---

