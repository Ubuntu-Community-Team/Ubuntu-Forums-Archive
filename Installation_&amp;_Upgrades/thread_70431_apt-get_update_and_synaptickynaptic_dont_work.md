---
title: "apt-get update and synaptic/kynaptic dont work"
date: 2005-09-29
forum: Installation &amp; Upgrades
---

### Post by rubenjavier on 2005-09-29
Hi, I've installed several times ubuntu/kubuntu in my home, and already used apt-get update and synaptic/kynaptic after chaging sources.list and allowrootlogin.
But yesterday I needed to install ubuntu in my work and they have the machines behind a windows proxy... after the installation, I wrote down the proxy IP and port and Ubuntu conected to the internet withou a problem... until I tried to do an apt-get update or synaptic/kynaptic.
I allways got the "couldn't stat sources packages list...."
I know that the repositories were down this weekend, but I got the message yesterday and today all day long.
I've just arrived at home an did a new breeze installation in another machine and apt-get update and synaptic worked perfectly (I tried at work with breeze and hoary)
I've also set at work the dns and gateway just in case there is something else needed besides the proxy configuration (but just with the proxy I could surf the net) but I cant get synaptic or apt-get update to work at my workplace
Is there something I need to know (is there some port I need to open at the windows proxy at work to be able to fetch the files)... or the repositories were down and I just got lucky and they were up when I got home an hour ago?
any help would be appreciated, I really need to get the machines to work under ubuntu at work
Thanks in advance

---

### Post by mlomker on 2005-09-29
I'm not sure how you configured your proxy.  [This has worked]("http://www.ubuntuforums.org/showpost.php?p=364026&postcount=2") for a couple people.

The update process just uses http or ftp, so you should have those working on your proxy server already.

---

### Post by rubenjavier on 2005-09-30
Im testing with Kubuntu right now, so I change the proxy settings on the network tab in system settings, there is a PROXY icon and it lets me put manually the HTTP, HTTPS and FTP IP address and port, I dont know right now if that info gets wrote down in the .bashrc file, but I can surf the net after the IP and port are set manually there (in the network settings tab)
When I get to work I'll check the .bashrc file to find out if the network settings tab writes down something there.
I dont think the proxy authenticates anything there, the domain do authenticate the windows machines to allow them to see the rest of the domain network, but I can see everything throug SAMBA with no problem.
Thanks a lot mlomker, I'll do the testing today and post the result

Just in case... if someone knows about a specific port that needs to be oppened on the proxy to do the apt-get update or use synaptic/kynaptic, please let me know
thanks

---

### Post by rubenjavier on 2005-09-30
OK I've tested here at work, and with the two extra lines in .bashrc I can use apt-get update in the console, but kynaptic still can't download the packages so I can't see the new packages downloaded trough apt-get update, I have no real problem with that, because I can use apt get to download the packages I need, but the rest of the users are new to Linux and the best solution is to have synaptic/kynaptic working for them... any Ideas?
obviusly .bashrc affect the configuration of the console<->net... but It doesn't affect the synaptic/kynaptic<->net configuration...
where does the synaptic/kynaptic<->net configuration is stored
I've already tried with the /etc/network/interfaces and /etc/resolv.conf and there is no visible proxy configuration
Thanks in advance.

---

### Post by mlomker on 2005-09-30
Add it to /etc/username/.bashrc as well.  If the lines are added to /etc/skel/.bashrc then that file will get copied whenever new users are created.

---

### Post by rubenjavier on 2005-10-01
Thanks again mlomker :) , at least that takes care of part of the problem.
Now I can use Kynaptics if I call it from the console (if I call it from the menu then it cant connect trough the proxy... weird ins't it?)
Now Im heading to the new forum of the kubuntu guys to check out if this is a KDE/Kubuntu issue, or is a Ubuntu configuration issue (why the desktop cant use the same proxy config that the console has???)
Really Thanks again... but if anyone already has the answer, then please post a reply.

---

### Post by dyrer on 2005-10-01
I dont use proxy server and i have the same problem

---

