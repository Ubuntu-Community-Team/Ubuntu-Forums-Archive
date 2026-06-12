---
title: "Fun times with Samba (please help)"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by thedarkend on 2006-02-21
I'm trying to setup samba to allow me to transfer files to and from my win 2k enabled laptop and my kubuntu server. Been working on it for most of the day and things just got amazingly fun.

Anyways long story short my samba server shows up on my windows box. But when I go to try and connect to my server it tells me "\\XXXXX is not accessible the network path was not found". I have already done the following steps..

1) Installed the samba package which does a complete install
2) Set up a test folder which is shared
3) Set up a samba user with a password
4) setup a common workgroup

Anyways in the end I've come to the conclusion that either I need to manually configure my /etc/samba/smb.conf and descrew whatever the gui setup in kde did. Or I need to try and setup a rule with iptables allowing for computers in my home network to connect to my server.

Now I said it was FUN so here is the best part. To see what it would be like the opposite way around I decided to set up a share on my laptop to be accessed by the server. 1 minute and a reboot later I went to the remote places folder and surprise almighty my laptop is listed. So I click on it and it prompts me for a password. Thinking to myself "this is way too easy" it suddenly connects me to my laptop and I am able to access all it's files and download anything and everything I want with ease.

So in the end I KNOW it's now possible. It's just figuring out now how to let the laptop access the server.

Much Thanks
thedarkend

---

