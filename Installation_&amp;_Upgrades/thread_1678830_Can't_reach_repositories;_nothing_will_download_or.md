---
title: "Can't reach repositories; nothing will download or install"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by boopit on 2011-01-31
Hey all. 

I'm on a fresh new install of Ubuntu 10.10. 

I can't install any updates, though; if I run 

```
sudo apt-get update
```

I get this:

```
Err http://extras.ubuntu.com maverick Release.gpg
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en          
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://extras.ubuntu.com maverick Release                              
Ign http://extras.ubuntu.com maverick/main Sources/DiffIndex               
Ign http://extras.ubuntu.com maverick/main i386 Packages/DiffIndex         
Ign http://extras.ubuntu.com maverick/main Sources                         
Ign http://extras.ubuntu.com maverick/main i386 Packages                   
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US
Get:1 http://archive.ubuntu.com maverick Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en            
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://extras.ubuntu.com maverick/main Sources
Hit http://archive.canonical.com maverick Release
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://archive.ubuntu.com maverick-updates Release.gpg
Ign http://extras.ubuntu.com maverick/main i386 Packages
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://extras.ubuntu.com maverick/main Sources
Hit http://archive.canonical.com maverick/partner Sources
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://archive.ubuntu.com maverick-security Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Hit http://extras.ubuntu.com maverick/main i386 Packages
Hit http://archive.canonical.com maverick/partner i386 Packages
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://archive.ubuntu.com maverick Release
Hit http://archive.ubuntu.com maverick-updates Release
Hit http://archive.ubuntu.com maverick-security Release
Hit http://archive.ubuntu.com maverick/main Sources
Hit http://archive.ubuntu.com maverick/restricted Sources
Hit http://archive.ubuntu.com maverick/multiverse Sources
Hit http://archive.ubuntu.com maverick/universe Sources
Hit http://archive.ubuntu.com maverick/main i386 Packages
Hit http://archive.ubuntu.com maverick/restricted i386 Packages
Hit http://archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick/universe i386 Packages
Hit http://archive.ubuntu.com maverick-updates/restricted Sources
Hit http://archive.ubuntu.com maverick-updates/main Sources
Hit http://archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://archive.ubuntu.com maverick-updates/universe Sources
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://archive.ubuntu.com maverick-security/restricted Sources
Hit http://archive.ubuntu.com maverick-security/main Sources
Hit http://archive.ubuntu.com maverick-security/multiverse Sources
Hit http://archive.ubuntu.com maverick-security/universe Sources
Hit http://archive.ubuntu.com maverick-security/main i386 Packages
Hit http://archive.ubuntu.com maverick-security/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-security/universe i386 Packages
Fetched 198B in 2s (86B/s)
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

If I try to run the update manager, it says "failed to download repository information, please check your internet connection"

There can't be anything wrong with my internet connection; I'm using the internet as I type this online.

How can I fix this?

---

### Post by garvinrick4 on 2011-01-31
It does not recognize the ones that have extras.ubuntu in them with gpg and translation.
put a # sign in front of them and save.
```
gksudo gedit /etc/apt/sources.list
```and put the comment sign (#) in front of to ignore them and
then save and run.
```
sudo apt-get update
```

---

### Post by sikander3786 on 2011-01-31
These type of errors i.e, resolve errors seem to appear where your router is configured as a DNS server itself and is unable to resolve some addresses. A workaround is to switch to Google DNS or OpenDNS for the time being and see if those errors go away.

See Linux instructions on this page.

[http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html)

Or sign up for Basic DNS here.

[http://www.opendns.com/start/](http://www.opendns.com/start/)

---

### Post by lewisskinner on 2011-02-01
> **garvinrick4 said:**
> It does not recognize the ones that have extras.ubuntu in them with gpg and translation.
put a # sign in front of them and save.
```
gksudo gedit /etc/apt/sources.list
```and put the comment sign (#) in front of to ignore them and
then save and run.
```
sudo apt-get update
```

I'm having a similar issue as well.  I wondered if I broke something on my system, so I performed a fresh install (even formatting my /home partition) and even now, running apt-get update, I get this:

```
Fetched 396B in 10s (36B/s)                                                    
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

I understand what you are saying, but will #commenting out those repos remove my access to some software?

---

### Post by sikander3786 on 2011-02-02
> **lewisskinner said:**
> I'm having a similar issue as well.  I wondered if I broke something on my system, so I performed a fresh install (even formatting my /home partition) and even now, running apt-get update, I get this:

```
Fetched 396B in 10s (36B/s)                                                    
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

I understand what you are saying, but will #commenting out those repos remove my access to some software?
Try changing your DNS server and let us know if that helps.

---

### Post by lewisskinner on 2011-02-02
Change how?  Is this within Ubuntu settings or my router's settings?

If I head to my router's setup utility ([http://192.168.2.1/](http://192.168.2.1/)) it will allow me to alter my DNS, but if I do, I cannot acccess the net.

sudo gedit /etc/resolv.conf just confirms that my nameserver is 192.168.2.1 (the router's IP).  Should I alter this to my ISP assigned IP?

---

### Post by lewisskinner on 2011-02-02
OK, scratch that.  When I edited resolv.conf and removed my router's IP and changed it to my ISP-assigned IP, I now do not get those failures on sudo apt-get update (except with medibuntu, until I reinstalled the key following the alterations).

First of all, why is this/how does this fix work?  I'm really a GNU/Linux n00b, so I'd like to learn *why* solution work, rather than just be told how to implement them.  Secondly, I do have a dynamic IP from my cable broadband provider (which I like, as it affords me some degree of anonymity), so what if it changes in the future?  It'll block me off the web, and by then I'll have probably forgotten where the config files are to edit, lol!

Anyone know a good way to maintain my web anonymity whilst I'm at it?

---

### Post by sikander3786 on 2011-02-02
That just happens because of the router's inability to translate adresses. Most of the time, it happens near the end of that apt-get update process. You need a proper DNS address to resolve addresses for you and not the router itself. Don't you?

You can then use your ISP's DNS servers, Google DNS or OpenDNS or any other.

If you doubt you'll forget the configuration later, you can just backup your resolv.conf and in case of a reinstall, restore it to its proper position.

```
sudo cp /etc/resolv.conf ~/Documents/resolv.conf
```

---

### Post by lewisskinner on 2011-02-03
I'll be honest, I'm not really technical.  I know what DNS means, but not how it works in practice.  I know my router is 192.168.2.1, and it assigns various devices on my network an IP, (PC is 192.168.2.2, fiancee's laptop 192.168.2.3, PS3 is 192.168.2.4, my mobile phone is 192.168.2.5 etc).  I assume though, that whichever of these accesses the internet, website will know  my main IP, and I also know that none of these match up to the DNS given by my router's config information.

Seriously, I'm a network beginner.

I did alter my /etc/resolv.conf though, but upon restart it changed back, so I write-protected it.  That ought to solve my issues anyway...

---

### Post by sikander3786 on 2011-02-04
Instead of editing your resolv.conf directly, you can use Network Manager to assign a manual DNS server. See the Linux instructions on this Google page.

[http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html)

For finding more about Domain Name System, this might help or you can do a Google.

[http://en.wikipedia.org/wiki/Domain_Name_System](http://en.wikipedia.org/wiki/Domain_Name_System)

Yes the router assigns IPs to all the systems on your network but those are internal IPs. Each system is also assigned a Public IP then.

[http://whatismyipaddress.com/](http://whatismyipaddress.com/)

And that is how your system is recongnized on Wide Area Networks i.e, Internet.

---

### Post by tak2100 on 2013-03-07
I had a similar problem.  Do you have an internet filter installed?  Something like OpenDNS filtering or Cybersitter can stop your PC from updating.  Whitelisting canonical.com seemed to work for me.  There might be other domains that need to be whitelisted as well.

---

