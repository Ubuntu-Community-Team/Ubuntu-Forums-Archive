---
title: "Problems with install of webmin"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by Streetwalker32 on 2006-11-15
On my new lamp server+gnome I try to install webmin.

When package installer starts I get this error:
Error: Dependency is not satisfiable: libauthen-pam-perl

What can be the problem ?

---

### Post by CasaDelNorte on 2006-11-20
I'm having the same issue with latest release (edgy eft) - continuing research. If anyone has an answer...

Cheers!

---

### Post by devnu11 on 2006-11-22
Ok, there is most likely another way to do this but the bottom line is it works to install webmin.

Go to [http://www.webmin.com](http://www.webmin.com)

In the upper right corner of webmin.com it says "Webmin Version" (something like 1.300) 

Below that is the release date (something like "15 September 2006") 

Last but not least is "Download TGZ RPM DEB."

You guessed it, download the deb package!

**Note the location where you download the package to (/home/username) for example.

**If this is a remote server follow the link to Sourceforge and copy the address for the server you choose.  Then use "wget www.sourceforge.net/webmin......(filename)......deb"

Via the command line (open a terminal or console window) type the following:

$ is your command prompt
> $ cd /directory where webmin.deb downloaded toThen 

> sudo dpkg -i webmin[version].debThis will install the webmin.deb but will not configure it YET.  It will produce an error telling deps have not been met.  Don't sweat it just yet!  Read on.

Next

> sudo apt-get -f installThe deps for webmin will then be installed if you type "y." You will then receive a message telling you how to log into webmin.

Enjoy.



________________________________________________
Women think men are a means of financial planning..... NOT!

---

### Post by dad311 on 2006-11-22
I downloaded the gzip file from webmin.com.  It installed on x86 and AMD64 without any issues.  Just unzip the file and run the setup script.

---

