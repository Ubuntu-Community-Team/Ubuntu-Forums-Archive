---
title: "After clean install 18.04 mount command from 16.04 not working"
date: 2018-09-16
forum: Installation &amp; Upgrades
---

### Post by twan2 on 2018-09-16
Hi, I recently did a clean install of LUBUNTU 18.04. When this machine was still on 16.04 I had figured out a mount command that would mount a shared drive on a WIN7 machine. This worked great. Now on LUBUNTU 18.04 I try the same command and it does not work. I am not very experienced in this area so I want to reach out for help. What can I do to figure out what the problem is?

This is the line that I use on the 16.04-system. I want to connect to shared folder "data2".
sudo mount -t cifs //192.168.1.116/data2 <my_home>/mnt/lan -o workgroup=WORKGROUP,username=<my_id>,password-<my_pw>

I have a second system that is still on 16.04, so I can look up stuff if that is required (but I wouldn't have a clue). 
Any help or suggestions are welcome...

---

### Post by ubfan1 on 2018-09-16
Have you installed the cifs-utils package on the new 18.04 system?

---

### Post by twan2 on 2018-12-28
Yes, the cifs-utils package is installed. I even uninstalled it and reinstalled, just to make sure this was not the problem.

My command-line looks like this:
mount.cifs //192.168.1.116/data2 /home/twan/mnt/lan -v -o credentials=.smbcredentials

My .smbcredentials look like this:
workgroup=WORKGROUP
username=<my-id>
password=<my-pw>

The result that I get is this:
Credential formatted incorrectly: WORKGROUP
mount.cifs kernel mount options: ip=192.168.1.116,unc=\\192.168.1.116\data2,iocharset=utf8,sec=ntlm,uid=1000,gid=1000,user=<my-id>,pass=********
mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

I really have no idea what is wrong here.

---

### Post by ubfan1 on 2018-12-28
Mabe add SAMBA to the title, you might get someone who can help.

---

### Post by twan2 on 2018-12-29
Look at the following link for a solution...[URL="https://ubuntuforums.org/showthread.php?t=2409187"]
https://ubuntuforums.org/showthread.php?t=2409187[/URL]

---

