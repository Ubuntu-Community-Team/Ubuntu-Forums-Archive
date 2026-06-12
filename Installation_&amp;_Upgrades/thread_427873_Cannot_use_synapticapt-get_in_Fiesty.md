---
title: "Cannot use synaptic/apt-get in Fiesty"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by simon jarman on 2007-04-29
Hi,
     I just upgraded my system from 'edgy' to 'fiesty' while maintaining my old '/home' partition. Everything works except my ability to access the Ubuntu software repositories. I go through a proxy server and have changed the settings for the whole system as well as for synaptic. I can access the internet with no problems, but any synaptic or apt-get attempts to get new software give this error:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/c/clustalw/clustalw_1.83-1.2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/c/clustalw/clustalw_1.83-1.2_i386.deb)
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

I don't know what the ISA server is. Is this a problem at my end? If so, how can I get around it?

Thanks in advance for advice.

---

### Post by jorno on 2007-09-10
I don't know if anyone still has this problem, but I found my solution in another post.

The steps mentioned here earlier are good and all, BUT if those of  you who's got this problem is in a Windows environment with a Microsoft ISA Proxy that need authentication, this is the solution that worked for me:

You need to install NTLMAPS.

[http://packages.ubuntu.com/feisty/web/ntlmaps](http://packages.ubuntu.com/feisty/web/ntlmaps)
* Go there, and download, either from within Firefox (if you manage to get Proxy working with Firefox - I did, but not apt-get or Synaptics or anything else).
* Download the package for ntlmaps (this is for Ubuntu Feisty)
* Start a terminal, find your downloaded package, and type:
*sudo dpkg -i ntlmaps_0.9.9.0.1-6_all.deb*
This should guide you trough the installation of the package...

BUT, my problems didn't stop there!
After, I had to edit /etc/ntlmaps/server.cfg manually.
( *sudo vim /etc /ntlmaps/server.cfg* )
Then I saw that the config-file was formatted with DOS (not UNIX), so I had to tell vim to convert it to UNIX-format. Do this in vim:
*:set fileformat=unix*
*:wq*
This should convert the file, and save it.
I also had to change some of the options:
Under the [CLIENT_HEADER] section, I had to comment out the first Accept and User-Agent part (Windows 98), and then uncomment the next part (Windows 2000 emulation).
Then I filled in "NT_HOSTNAME" (remembered what PC number this workstation had in Windows), and "NT_DOMAIN").

After those changes, restart ntlmaps:
*/etc/init.d/ntlmaps restart*

And point all your proxy-settings to: [http://127.0.0.1:5865](http://127.0.0.1:5865)

Make a file: */etc/apt/apt.conf*
Acquire::http::Proxy "http://127.0.0.1:5865";

And then try "*apt-get update*".

You could also insert this into:
System -> Preferences -> Network Proxy

And in Synaptics:
System -> Administration -> Synaptics -> Settings -> Preferences -> Network:
Manual proxy configuration:

127.0.0.1 port 5865 (no authentication)


I recommend NOT using the NTLMAPS-proxy for browsing with Firefox, as I found it to cause some problems. Often Firefox manages to connect correctly with the Proxy by itself, after configuring it to do so: Edit -> Preferences -> Advanced -> Network.

This should do the trick! It did for me.. Please ask if there is something not clear yet, or if I should correct any of this. (Sorry, English is not my native tongue).

---

