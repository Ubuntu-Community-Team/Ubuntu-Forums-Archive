---
title: "Partitions and linux folders"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by lordjeremias on 2008-05-20
Hi everyone.
i've just started using ubuntu a couple of weeks ago and i'm quite hppy with the result, faster, lighter and safer than windows. i'm now preparing to do a full switch to linux, leavin the win partition for some games and special tasks.
my questions relate to the folders in linux and the partitions mount:
[LIST=1]
planning to have a separate home partition in order to protect my data. what goes in the home folder? only my personal documents that i save there or also some configs and application data? if this application data is stored in my home folder, can i have it stored somewhere else?

[*] what exactly is stored in the /var folder? i've read some posts refering to it as in need of a separate folder for mail. is the email from users stored in there? where exactly is the email stored?

[*] and in the /usr folder?

[*] i want to keep my music colection acessible to all users in a easy way (for example appearing in the links when you open a save box) is there some special "public" folder in linux? kind of shared documents in windows?

[*] and if not, is there any way i can mount that mp3 folder as the music folder in EVERY user? not just /home/user1/musicfolder but kind of /home/user*/musicfolder?
[/LIST]

and just off the record ;) , is Wine or Cedega anygood for running games in linux? could i play Far cry (old pc...) or GTA San Andreas in it, considering it already has some speed limits in windows?

thank you all for your support! i'm just a noob in linux but i'm learning!...

---

### Post by mikewhatever on 2008-05-20
For explanations on what various directories are for, check out the following links:
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html)
[http://www.google.co.il/search?q=linux+directory+structure+standard&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.il/search?q=linux+directory+structure+standard&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

Your home directory is for personal files and settings, but you don't have to keep files there. It might be more convenient to keep files on a separate data partitions.
The same goes for music. You could make a separate music partition aoutmounted at startup. Access rights can be given all users with chmod -R 777 command (see <man chmod>. There is no need to mount that partiton individually for every user.
If you prefer to have a music directory instead of partition, simply create it under / and give all users permissions to access it with the above mentioned chmod.
[Good permissions guide.]("http://www.linuxforums.org/security/file_permissions.html")

---

