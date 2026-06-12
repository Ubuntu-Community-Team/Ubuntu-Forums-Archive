---
title: "DVD 7.04 (network install - local respository)"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by ravingmad on 2007-09-02
Hi all

I must say I am new to Ubuntu so bear with me. I have spent the whole day reading through forum posts and various other resources on the Internet. First off I wanted to give Ubuntu a real try by loading it on an older laptop. I downloaded the entire DVD version of 7.04 at a friends place because he has an uncapped connection.

I started installing it this afternoon and turns out the laptop DVD-rom had a problem installing from the DVD. I then read a number of posts about network installs and after several hours and a few posts in the right direction I managed to get the network install working.

I setup the DVD source as a local repository, had to eventually disable IIS and use Apache and finally the installer would read files from the network. (PS - running the repository off a Windows 2003 Server)

I then encountered a number of errors during the install. namely packages that were not downloading. I then checked the Apache logs and found a number of files whose extensions were not named correctly. For instance if the installer was looking for xxx.udeb ... the file in the repository was xxx.deb or xxx.d ... a bit or trial and error, renaming those file as they occured and finally got the system installed. I have a suspicion that extracting the ISO using Winrar might be the cause but I will confirm that later by extracting it with Isobuster and running a compare.

Then it asked me "next step of installation" so I chose "install software" (or something like that), I chose all 3 options. The installer then stopped at 6% ... for a while. I then checked my firewall and saw that it was downloading a number of files from the Internet. 

I am on a Vodacom 3G connection and this thing just downloaded a bunch of files without notifying me. Luckily it was not too much but a "little" heads up from the installer would be nice. Perhaps the creators could build a little more details of this type of thing into the installer?? Maybe a message like "the files you want to install are not located in the repository you have selected - download them from Internet YES/NO" ...... also ... surely the DVD version would contain everything?

Overall, it has been quite a day getting this installed without a DVD-rom drive. Of course if I did have a functioning DVD-rom it would have been installed in a snap no doubt but still it was a challenging yet interesting experience. 

For those people using a Windows machine as the source for a network install, it can be done. Hopefully below will help someone one day with this exact scenario.

1 - Use TFTP.exe to serve as a network boot DHCP (instructions at this post) - [http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows](http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows)

2 - Disable IIS (temporarily) - IIS has problems with some of the file name and file structures

3 - Extract the ISO to a folder on your harddrive (approx 7.5GB of space needed)

3 - Install Apache HTTP, edit the http.conf file change the "Document Root" (line 149) to the folder on your harddrive where you extracted Ubuntu and also change line 177 to the same directory. Do not use backslashes eg. c:\ubuntu must be in the http.conf file as c:/ubuntu

4 - Around line 203 of the http.conf file add "Allow from x.x.x.x" where XXX is the IP address of the computer you are installing from. OR (but be careful) you can say "Allow from all"

5 - Check that you can access this in your browser. (depends on how you config'd your apache)

5 - Then start TFTP.exe

6 - Set the remote machine to boot from network (check in your bios settings)

7 - It should boot from network and start installing.

A couple of posts that helped me out (which may help someone else in turn one day):
-----------------------------------------------------------------------------------
[https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)
[http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows](http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows)
[http://ubuntuforums.org/showthread.php?t=332343](http://ubuntuforums.org/showthread.php?t=332343)
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

---

