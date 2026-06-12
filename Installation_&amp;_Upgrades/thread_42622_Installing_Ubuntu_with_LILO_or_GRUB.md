---
title: "Installing Ubuntu with LILO or GRUB"
date: 2005-06-18
forum: Installation &amp; Upgrades
---

### Post by itxweather on 2005-06-18
Hi,

Please excuse my ignorance but i'm a complete newbie to Linux and would really like to install Ubuntu Linux however don't want the installation to over-write an existing hard disk partition & Operating System. 

What i'd like to ask is whether or not there is documentation that advises step by step how to go about doing this using a boot loader such as LILO or GRUB (think that's what they're called).

I think that the "expert" option needs to be chosen however as i'm by no means an expert I do not want to over-write my existing partition.

Really impressed with the Live CD version of Ubuntu and would like to learn a lot more about Ubuntu Linux.

Your comments would be appreciated.
Thank you.

Best Regards.

---

### Post by irusun on 2005-06-18
Sorry, I don't see an install guide either (if there is one, it's obviously too hard to find).  But maybe I can give you a few pointers.

First, before doing anything - make sure to back up all your critical data on the hard drive.  Whether you know what you're doing or not, accidents happen.

You're going to need a free partition for Ubuntu and a free partition for the Swap before you can install (without wiping out your other partitions - I assume that other OS is Windows).  The basic premise is that you need to shrink the existing partition on your drive to make room for the new ones.

You'll need to use a partition utility to do that - I think the Unbuntu installation CD includes one, but you might be more comfortable using a commercial software package if you're not familiar with the process.  This isn't strictly related to Ubuntu, so you can search these forums as well as google it.

You'll want a partition size of several gigabytes for the Ubuntu partition and about a gigabyte for the Swap (swap size should usually be about double the RAM).

Once that's completed, it's pretty straight forward.  You'll want to enter the "expert" mode.  You should see a list of the partitions on the drive.  Select the proposed Ubuntu partition and make it root "/".  Select the proposed swap partition and make it swap.  That's about all there is too it.

---

### Post by Xian on 2005-06-18
[QUOTE=itxweather]What i'd like to ask is whether or not there is documentation that advises step by step how to go about doing this using a boot loader such as LILO or GRUB (think that's what they're called)[/QUOTE]
Here's the install guide on [Making Your System Bootable](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch06s03.html#di-make-bootable).

---

### Post by irusun on 2005-06-18
Wow, that's a pretty interesting resource.  How would a new user find that on their own?

---

### Post by itxweather on 2005-06-18
[QUOTE=irusun]Sorry, I don't see an install guide either (if there is one, it's obviously too hard to find).  But maybe I can give you a few pointers.

First, before doing anything - make sure to back up all your critical data on the hard drive.  Whether you know what you're doing or not, accidents happen.

You're going to need a free partition for Ubuntu and a free partition for the Swap before you can install (without wiping out your other partitions - I assume that other OS is Windows).  The basic premise is that you need to shrink the existing partition on your drive to make room for the new ones.

You'll need to use a partition utility to do that - I think the Unbuntu installation CD includes one, but you might be more comfortable using a commercial software package if you're not familiar with the process.  This isn't strictly related to Ubuntu, so you can search these forums as well as google it.

You'll want a partition size of several gigabytes for the Ubuntu partition and about a gigabyte for the Swap (swap size should usually be about double the RAM).

Once that's completed, it's pretty straight forward.  You'll want to enter the "expert" mode.  You should see a list of the partitions on the drive.  Select the proposed Ubuntu partition and make it root "/".  Select the proposed swap partition and make it swap.  That's about all there is too it.[/QUOTE]

Hi Irusun,

Thank you for your reply. With regards to resizing an existing partition are there any partition managers that you'd recommend (Is Partition Magic worth a try?).

Thank you.
Best Regards.

---

### Post by itxweather on 2005-06-18
[QUOTE=Xian]Here's the install guide on [Making Your System Bootable](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch06s03.html#di-make-bootable).[/QUOTE]

Hi Xian,

Thank you for your reply. Much appreciated.

Best Regards.

---

### Post by irusun on 2005-06-18
[QUOTE=itxweather]With regards to resizing an existing partition are there any partition managers that you'd recommend (Is Partition Magic worth a try?).[/QUOTE]

Partition Magic is definitely one of the most popular.  I'm currently using Paragon's Partition Manager - it has some native Linux support and a liberal policy on creating bootable CDs and the Windows portion of if works nicely.  But any of these will work well... you can find reviews all over the net.

[http://www.paragon-gmbh.com/index.htm](http://www.paragon-gmbh.com/index.htm)
[http://www.v-com.com/](http://www.v-com.com/)
[http://www.symantec.com/partitionmagic/](http://www.symantec.com/partitionmagic/)

That's it for me.  Good luck!

---

### Post by mohaham on 2005-06-18
while installing Ubuntu you can specify what partition you would like to use for root
and Ubuntu gets installed in that partition, and then u can install GRUB in the MBR when prompted..

---

### Post by itxweather on 2005-06-19
[QUOTE=irusun]Partition Magic is definitely one of the most popular.  I'm currently using Paragon's Partition Manager - it has some native Linux support and a liberal policy on creating bootable CDs and the Windows portion of if works nicely.  But any of these will work well... you can find reviews all over the net.

[http://www.paragon-gmbh.com/index.htm](http://www.paragon-gmbh.com/index.htm)
[http://www.v-com.com/](http://www.v-com.com/)
[http://www.symantec.com/partitionmagic/](http://www.symantec.com/partitionmagic/)

That's it for me.  Good luck![/QUOTE]

Hi Irusun,

Thank you for the URLs. much appreciated. I've installed Ubuntu and over-written the existing operating system as needed a clean install, however i'd like to be able to dual-boot so need to know as much as possible about using a partition manager.

I'm impressed with Ubuntu, particularly as it'd correctly identified and installed drivers for all hardware, admittedly two 802.11b WLAN PCCards did not work however a 3Com 802.11g WLAN PCCard does work.

One problem i'm having right now (apologies if I really should post a new thread), something very unusual is happening with Firefox, basically if a hyperlink is clicked on from let's say the default Ubuntu homepage, Firefox re-directs to that particular URL, the same as a google search can be done, however if a URL is manually entered into the address bar a "connection is refused" error message appears.

Whilst i'm a complete Linux newbie (however am willing to learn), i'm convinced that the problem has something to do with the way that Firefox has been configured, the reason why I say this is because I can successfully ping web-sites that the browser won't allow me to visit, the same goes for checking a domain name in the whois search.

Can anyone offer any suggestions as i'd really like to get Ubuntu Linux up and running properly and be able to browse the internet without any of the problems that are persisting with Firefox.

I've not changed any settings on my D-Link Ethernet Modem/Router and am using DHCP as opposed to a dynamic IP address. There were no problems with connecting to the internet using Firefox running on the operating system previously installed.

Thank you.
Kind Regards.

---

### Post by mingus on 2005-06-20
Re your Firefox problem:  Happening with all url's or just a few?  Ping uses udp, and whois is a dns server query - neither test an http connection.  If you get "could not be found", means the url is bad or the connection is broken.  If you get "connection refused", means web server received your request but the reply is being blocked.  Using a proxy?  ISP using filters?  Firefox should auto-configure when it installs; if you just installed Ubuntu from CD you'll want to upgrade it anyway - you'll need to do this from the backports repository (see Starter Guide and Forum).

Re your Wireless cards:  It is the card's chipset which determines the driver used, so you'll need to determine that.  Easily googled.  Some are linux friendly (Prism), others take a bit more work (TI), others impossible.

---

### Post by itxweather on 2005-06-20
[QUOTE=mingus]Re your Firefox problem:  Happening with all url's or just a few?  Ping uses udp, and whois is a dns server query - neither test an http connection.  If you get "could not be found", means the url is bad or the connection is broken.  If you get "connection refused", means web server received your request but the reply is being blocked.  Using a proxy?  ISP using filters?  Firefox should auto-configure when it installs; if you just installed Ubuntu from CD you'll want to upgrade it anyway - you'll need to do this from the backports repository (see Starter Guide and Forum).

Re your Wireless cards:  It is the card's chipset which determines the driver used, so you'll need to determine that.  Easily googled.  Some are linux friendly (Prism), others take a bit more work (TI), others impossible.[/QUOTE]

Hi Mingus,

Thank you for your reply. Much appreciated. Was thinking of putting together a new thread as this one might not necessarily be read under the title of "Installing Ubuntu with LILO or GRUB", if you think that a new thread or post should be posted please let me know.

The Firefox problem appears to be happening with just about all URL's that are manually typed, from what I can remember right now a hyperlink on the default homepage which re-directs to Ubuntu.com works as does a google search however just about all of the URL's manually entered into the address bar result in a "connection refused" error message.

Hadn't realised that pinging or whois use http, thank you for that, still a lot to learn!.

With regards to "Using a proxy?  ISP using filters?", i'm not 100% sure how to answer this one, afaik i'm not using a proxy and my ISP isn't using filters, however, could you please suggest how I can check to make sure?. My isp is EFHbroadband.com.

With regards to upgrading the Ubuntu installation any idea's how I can go about doing this considering that my internet connectivity doesn't appear to be working correctly?. Shall read through what you've suggested I read through in the backports repository though.

Thank you for your help. Once again much appreciated.
Best Regards.

---

### Post by mingus on 2005-06-20
If you are able to ping and do a whois, you have a tcp/ip connection. 
 
*"Hadn't realised that pinging or whois use http"* - actually it's the other way around.  And to be precise, a whois that is done from a browser uses http but from a command line may not, like a ping.

By the way, are you using a firewall?  If so, try turning it off.

Try doing this in the firefox browser address bar:
[ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/)
You should see a short list of folders/names and a column of dates. 
Now change the url from "ftp" to "http": 
[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
you should see the same names, but no icons, no date columns - and Apache below

In the first command you are using the ftp protocol and the page has been served by the Ubuntu ftp server.  The second page tests the http protocol, with the page being served by the apache web server.  Tell us what happens.

Also, if the http url works, so will your repositories (take a look at /etc/apt/sources.list).  If http does not work but ftp does, then you can probably change the http to ftp in your sources.list.  Both of these are pointing at the same files, just via 2 different servers.  After you get your problem resolved, change back to http because it's a tad faster.

Since you're probably able to download, beside upgrading firefox you can also try installing another browser.   Probably Galeon and Epiphany are out there, and lynx or links which are text mode browsers (don't use html).  If you can replicate the problem in another browser, the issue is elsewhere in your configuration.

---

### Post by itxweather on 2005-06-20
[QUOTE=mingus]If you are able to ping and do a whois, you have a tcp/ip connection. 
 
*"Hadn't realised that pinging or whois use http"* - actually it's the other way around.  And to be precise, a whois that is done from a browser uses http but from a command line may not, like a ping.

By the way, are you using a firewall?  If so, try turning it off.

Try doing this in the firefox browser address bar:
[ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/)
You should see a short list of folders/names and a column of dates. 
Now change the url from "ftp" to "http": 
[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
you should see the same names, but no icons, no date columns - and Apache below

In the first command you are using the ftp protocol and the page has been served by the Ubuntu ftp server.  The second page tests the http protocol, with the page being served by the apache web server.  Tell us what happens.

Also, if the http url works, so will your repositories (take a look at /etc/apt/sources.list).  If http does not work but ftp does, then you can probably change the http to ftp in your sources.list.  Both of these are pointing at the same files, just via 2 different servers.  After you get your problem resolved, change back to http because it's a tad faster.

Since you're probably able to download, beside upgrading firefox you can also try installing another browser.   Probably Galeon and Epiphany are out there, and lynx or links which are text mode browsers (don't use html).  If you can replicate the problem in another browser, the issue is elsewhere in your configuration.[/QUOTE]

Hi Mingus,

Thank you for your reply.

*"Hadn't realised that pinging or whois use http" - actually it's the other way around.  And to be precise, a whois that is done from a browser uses http but from a command line may not, like a ping.*

Apologies, think i'd got confused here :-(. Thank you for clearing up what i'd mis-interpreted though.  :smile: 

*By the way, are you using a firewall?  If so, try turning it off.*

Have just this minute checked and the firewall and NAT service are enabled on the D-Link 604-T Ethernet Router that i'm using to connect to my isp. I've disabled this and shall check whether or not it's made any difference.

Once i've checked whether or not switching off the firewall i'll re-post on this thread. I'd like to switch back on the firewall though admittedly, can Ununtu/Firefox be configured so that internet connectivity works with the firewall switched on?.

Thank you.
Best Regards.

---

### Post by mingus on 2005-06-20
[QUOTE=itxweather]Have just this minute checked and the firewall and NAT service are enabled on the D-Link 604-T Ethernet Router that i'm using to connect to my isp. I've disabled this and shall check whether or not it's made any difference.

Once i've checked whether or not switching off the firewall i'll re-post on this thread. I'd like to switch back on the firewall though admittedly, can Ununtu/Firefox be configured so that internet connectivity works with the firewall switched on?[/QUOTE]

Yes, it should work.  What we're doing is using a process of elimination to isolate where the problem is.  There are a number of possible reasons for the browser issue.  So we want to test whether its *this* browser vs *any* browser, whether the firewall or router configuration is the source, etc.

BTW, one of my routers is a DI-614+.

---

### Post by itxweather on 2005-06-20
[QUOTE=mingus]Yes, it should work.  What we're doing is using a process of elimination to isolate where the problem is.  There are a number of possible reasons for the browser issue.  So we want to test whether its *this* browser vs *any* browser, whether the firewall or router configuration is the source, etc.

BTW, one of my routers is a DI-614+.[/QUOTE]

Hi Mingus,

Thank you for your reply. I've switched off the Firewall & NAT Service and unfortunately still am unable to connect to the internet only to my D-604T.

Could you please confirm that the connection settings in Firefox should be "Direct connection to the internet".

What settings should be against "Eth 1", i've chosen to use DHCP as opposed to entering a static ip and chosen the gateway to be the same ip address as my D-604T.

Have noticed that whilst the Firewall & NAT Service is switched off i'm unable to Ping an ip address and am also unable to use Whois. 

Is there anything obvious that I must check prior to running the checks you'd mentioned earlier this evening?.

Thank you.
Best Regards.

---

### Post by mingus on 2005-06-21
Not sure, but I think when you say turning off the NAT service you mean you are disabling the DHCP server in the router - that definitely will result in your not being assigned an IP address and therefore not connecting to the net.  That is why you are not getting a response to your pings beyond the router.

In a terminal do $sudo ifconfig - you will see eth1 and should see the LAN address the router has assigned.  If there is not one there, make sure DHCP is active in the router and that in Ubuntu you've set eth1 to DHCP, reboot, and you should be back online.

On your computer you do not usually need to specify a gateway address when you are using DHCP - I don't in my Ubuntu configuration.  Your network adapter should find the router.

Again re "connection refused" in Firefox.  If you google this, you will find quite a few different possible causes and similar diagnostic suggests to prev posts.  Most are due to M$ issues.  Other possibilities:
* Incorrectly configured proxy
* Corrupted Firefox profile (reinstall)
* Firewall blocking ports (make sure you don't have any filters active or ports blocked)
* ISP blocking (usually parental controls or spam, but sometimes the ISP messes this up or mistakenly blocks an IP.  Suggest you check with yours, *especially* if the ISP supplied router).

When you try another browser, you'll determine if Firefox is the culprit.

After making sure there is nothing blocking anything in the router, reboot it.  D-Links have been known to get confused.  A few times I have had to do a hard reset to the router to clear it out (note: the European version of the Di-604 is diff from the U.S. version; check locally for how to do a reset).

---

