---
title: "Problem Installing Tor on lubuntu (lucid) 10.04"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by odoncaoa on 2010-08-14
Greetings All,

I'm attempting to install Tor on a relatively new file system (Gateway LT3114u). And, I've employed 'https://www.torproject.org/docs/debian, and 'http://ubuntuguide.org/wiki/Ubuntu:Lucid', and 'http://languor.us/installing-and-setting-tor-privoxy-kubuntu-firefox' as install referrences. The new install is to an lubuntu system, which did not include 'tor' via it's  'Synaptic Package Mgr' (although it does include 'tork' & 'vidalia'?). Consequently, I employed Synaptic to implement the management of the package update, relative only to packages that had previously been installed. Thus, the system appears not to be gaining access to the correct, relevant data for the 'tor' install. So, I'm wondering if anyone might know what needs to be done, in order to  undue, or work around, the current feaux pas?

Cheers, :confused:


	$ sudo gpg --keyserver keys.gnupg.net --recv 886DDD89
	gpg: WARNING: unsafe ownership on configuration file `/home/odoncaoa/.gnupg/gpg.conf'
	gpg: external program calls are disabled due to unsafe options file permissions
	gpg: keyserver communications error: general error
	gpg: keyserver receive failed: general error
	
	$ sudo gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
	gpg: WARNING: unsafe ownership on configuration file `/home/odoncaoa/.gnupg/gpg.conf'
	OK
	
	$ sudo apt-get install tor
	[sudo] password for odoncaoa: 
	Reading package lists... Done
	Building dependency tree       
	Reading state information... Done
	Package tor is not available, but is referred to by another package.
	This may mean that the package is missing, has been obsoleted, or
	is only available from another source
	E: Package tor has no installation candidate
	
	
	$ sudo apt-get install tor tor-geoipdb
	Reading package lists... Done
	Building dependency tree       
	Reading state information... Done
	Package tor is not available, but is referred to by another package.
	This may mean that the package is missing, has been obsoleted, or
	is only available from another source
	E: Package tor has no installation candidate

---

### Post by keylokes on 2010-08-14
did you do 

"sudo apt-get update"

i Just installed Lubuntu on my old crappy laptop .. running Awesome!! now..

and i had the same problem with a couple of programs i wanted until  i did "update" ..

so maybe that.??

---

