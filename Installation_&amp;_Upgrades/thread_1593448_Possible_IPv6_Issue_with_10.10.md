---
title: "Possible IPv6 Issue with 10.10?"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2010-10-11
Installed 10.10 on two PCs. Install was very smooth but both Firefox and Opera browsers load pages slow again. This seems to happen after every time I upgrade to a newer version of Ubuntu. Suspect it is an IPv6 issue again. Once IPv6 is disabled browsers load pages very fast again. 

Anyone have the code to correct this issue for 10.10?

---

### Post by efflandt on 2010-10-11
I originally installed 64-bit 10.10 beta, upgraded to RC, updated to what is probably release.  And in System > Preferences > Network Connections I think ipv6 was set to "Ignore" by default for Auto eth0.  At least I don't remember even looking at that before you mentioned it.

---

### Post by cybrsaylr on 2010-10-11
efflandt,
Checked in System > Preferences > Network Connections and ipv6 was set to "Ignore".

Firefox seems to load pages a bit faster than Opera but Opera really crawls. But both FF and Opera loaded pages much faster on 10.04 than 10.10.

---

### Post by moore.bryan on 2010-10-11
I noted this, too, and ran the trusty ```
cat /proc/sys/net/ipv6/conf/all/disable_ipv6
```which returned a 0 indicating ipv6 was turned-on. Without going through the traditional turn-off methods, I wanted to first see if there were any other workarounds.

I've found relief by unchecking the "Require IPv4 addressing for this connection to complete" box in network preferences. Basically, the pop-up tells me checking the box "allows the connection to complete if IPv4 configuration fails but IPv6 configuration succeeds, when connecting to IPv6-capable networks."

---

### Post by cybrsaylr on 2010-10-11
I also got a 0 when putting in 
> cat /proc/sys/net/ipv6/conf/all/disable_ipv6

I then unchecked: "Require IPv4 addressing for this connection to complete" box in network preferences but got no relief. Browsers are still slow.

When going to YouTube it takes ~40-55 seconds for every clip to play where in the past clips played in a second or two after being selected.

---

### Post by moore.bryan on 2010-10-11
Hmm... I'm not getting much of a delay at all. Are you sure it's not on your network?

---

### Post by cybrsaylr on 2010-10-11
OK I just discovered it is definitely an Ipv6 issue.

Just fixed Firefox which loads up YouTube clips fast like normal again by doing this which I got off this thread:
[http://ubuntuforums.org/showthread.php?t=1590490&highlight=disable+IPv6+Firefox](http://ubuntuforums.org/showthread.php?t=1590490&highlight=disable+IPv6+Firefox)

> Type into Firefox browser, about:config
then type in the filter box: ipv6
and disable it when it comes up.

Click on that line to change the value from 'false' to 'true'

I did this and FF flies again now for 10.10.

Opera still goes slow and have to figure out how to disable IPv6 for Opera.

---

### Post by annoyingrob on 2010-10-12
I'm not noticing any slowdown whatsoever on chromium and 10.10, although I'm actually running an IPv4/IPv6 network.

What's interesting is if IPv6 is set to ignore (it's default setting in the network manager), it will get its IPv6 address from my server, and be able to access IPv6 sites just fine. If i set it to "automatic", IPv6 doesn't work at all.

---

### Post by cybrsaylr on 2010-10-12
Haven't put Chrome in yet.
Firefox is running fast now.
Seem to recall having this same slowness problem with Opera before. Unfortunately ipv6 can't be disabled on Opera as easily as with FF.

---

### Post by cybrsaylr on 2010-10-13
Anyone know how to disable ipv6 in Opera 10.62?

---

### Post by moore.bryan on 2010-10-13
After playing around with some settings, I'm fairly convinced this isn't really an IPv6 issue, but a DNS lookup issue. Even though I have dnsmasq installed, it seems to still be slow in making lookups.

---

### Post by cybrsaylr on 2010-10-14
Ran into this bug before with Opera. Opera does things a little differently with their browser. I started a thread on this in the Opera Forums for help. Unfortunately the Opera forums are not as active as Ubuntu forums.

---

### Post by cybrsaylr on 2010-10-16
Was having some intermittent problems with pages loading slow at times with Opera with Karmic Koala on my main PC. I remembered about checking, them changing some Opera settings in 'change path' in Plug-in Options:

Tools > Preferences > Advanced > Content > Plug-in Options > Change Path.

There were two options checked.
Recalled someone saying this may cause a problem.
I unchecked one and left '/usr/lib/flashplugin-installer' as the only option checked and Opera is performing much better on Karmic with that intermittent slowness gone.

Tried this same solution on 10.10 but it did not work on 10.10 which is still slow.

---

### Post by cybrsaylr on 2010-10-17
Anybody have a solution to speed up Opera on 10.10?

---

### Post by cybrsaylr on 2010-10-23
Can anyone help on speeding up Opera?

---

### Post by moore.bryan on 2010-10-23
I don't use Opera much and don't know many who do... but have you tried the [Opera Forums]("http://my.opera.com/community/forums/") to see what suggestions they have?

---

### Post by cybrsaylr on 2010-10-23
I have tried the Opera Forums and got no help other than telling me to try Opera 11 alpha. This is unusual because there were a couple guys who used to help in the past. Opera has been my fav for 10 yrs because Opera is usually faster than FF and Chrome. I use them all to keep up on them. This 'slowness issue' has happened in the past with Opera and is usually corrected. Hoping they fix it soon because right now Opera only runs slow on 10.10. On 9.10 Opera 10.63 flies faster than FF and Chrome.

---

### Post by moore.bryan on 2010-10-24
That's what I love about Linux... no matter what benchmarks and tests anyone does to tell the community the "fastest" browser, things still depend on your individual system! :-)

Sorry about the slowness... I think of anything, I'll repost.

---

### Post by cybrsaylr on 2010-10-25
Well at this point it appears to be an Opera issue since FF and Chrome run fine. Opera does things a little different. Just hope Opera finds a remedy soon.

---

### Post by cybrsaylr on 2010-11-05
How to Disable IPv6 in Linux.

Got this off the Opera Forums today: [http://my.opera.com/community/forums/topic.dml?id=792362&page=1#comment7599242](http://my.opera.com/community/forums/topic.dml?id=792362&page=1#comment7599242)

[http://translate.google.de/translate?u=http%3A%2F%2Ftrompetenkaefer.wordpress.com%2F2009%2F12%2F15%2Fipv6-unter-linux-deaktivieren%2F&sl=de&tl=en&hl=&ie=UTF-8](http://translate.google.de/translate?u=http%3A%2F%2Ftrompetenkaefer.wordpress.com%2F2009%2F12%2F15%2Fipv6-unter-linux-deaktivieren%2F&sl=de&tl=en&hl=&ie=UTF-8)

> Disable IPv6 in Linux

So you can switch among the various distributions IPV6: 

Debian / Sidux / Ubuntu / Linux Mint: 

As root / etc / modprobe.d / aliases to open the 
and the line 

alias net-pf-10 ipv6 
in 
alias net-pf-10 off 
. Change 

To load the ipv6 module to prevent the manual nor the line can be attached off ipv6 alias. 

Product Squeeze / newer Ubuntu releases 

Insert if Grub2 following line in the file / etc / default / grub: 

#IPV6 aus 
GRUB_CMDLINE_LINUX="ipv6.disable=1" 

When Grub (1) in / boot / grub / menu.lst the following to the kernel append line: 

ipv6.disable=1 

And yet another update-grub run and thereafter. 

Archlinux 

In the file / etc / modprobe.d / modprobe.conf line 

#Laden von IPV6-Modul verhindern 
alias net-pf-10 off 

. Insert 

Fedora 12 (probably also applies to RedHat Enterprise CentOS 6 + 6) 

the file / etc / modprobe.d / blacklist.conf Write in the following lines: 

# ipv6 deaktiviert 
blacklist ipv6 
install ipv6 /bin/true 

OpenSUSE 11.2 

Since IPv6 compiled into the kernel and has been found to disable Yast can not, you have to Grub 
/ Boot / grub / menu.lst Append the parameters ipv6.disable = 1. 

Firefox / Iceweasel 

This also must be disabled IPV6 in Firefox is one inthe address bar about: config enter, then the string value to true the network.dns.disableIPv6

Read it over and not sure how to use it in my application.
Can anyone help out and show the easy way to use it?

---

### Post by moore.bryan on 2010-11-06
FYI: There is no /etc/modprobe.d/aliases file in 10.10.

---

### Post by cybrsaylr on 2010-11-06
Thanks for that info moore.bryan.

Still wading through that post to figure it out.

---

### Post by areynaldos on 2010-12-18
After looking around in many places, this was the solution for me:

[http://my.cn.opera.com/community/forums/topic.dml?id=792362&t=1292670826&page=1#comment8085062]("http://my.cn.opera.com/community/forums/topic.dml?id=792362&t=1292670826&page=1#comment8085062")

---

