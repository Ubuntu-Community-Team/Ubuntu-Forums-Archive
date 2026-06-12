---
title: "Samba stopped working on lucid upgrade"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by Slates on 2010-07-27
I just upgraded from 9.1 to 10.04. After doing this I have encountered issues with samba shares(like they dont work anymore !), which I previously used quite happily (from my windows XP boxes).
  Specifically, 
  On trying to share a folder in the gui I get 

/var/run/samba needs permissions 0755 to run. 

Easy to change, which I do, but why do I need to ? Plus it also returns when I reboot. Seems odd, never used to happen ?

    Continuing on, the next error I get on trying to share is 
  'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.
  So I jump to the command line and try sudo /etc/init.d/samba restart but get command not found. That’s how I restarted Samba on 9.1 – but now something is wrong ?Does Samba now work differently, or has my memory failed me ?


  But I know from searching this error can be caused by permissions, and, because I have another upgrade issue in that my keyboard (local or via NVC) no longer generates caps lock or shifted keys, I have changed my shell password to suit while I diagnose this problem. Accordingly I jump into smbpasswd to likewise change it but get told 
  [FONT=&quot]Unable to connect to SMB server on machine 127.0.0.1. Error was : NT_STATUS_CONNECTION_REFUSED.[/FONT]
  
 

All I can think of is my hosts file where I added the local machine name as a host to 127.0.0.1 in addition to local host. That cant make a difference, so I take it out again, but it makes no difference.
I also notice that I now cant even see my Ubuntu machine on my windows network (although I can see my windows shares from the Ubuntu desktop  gui), whereas I always could, of course.ow I’m really puzzled.  and indeed it doesn’t.
   I think this points to my samba setup not working or not being set up correctly.

    So now I uninstall samba. And reinstall it again. But the same symptoms persist. 
    I realized Im stumped when I cant even run samba up through /etc/init.d/samba start like I used to (and as per the installation and usage wiki pages). That was about the time I though I should call me for help to get me back on the right track.
  Anyone know where Im going worng here ? .All I did was upgrade [FONT=Wingdings]:-)[/FONT]

---

### Post by phillw on 2010-07-27
Hi, this is on my lubuntu area as we were trying to get pyneighborhood to work, but it will work across any of the *buntu family.

[http://forum.phillw.net/viewtopic.php?f=18&t=96&p=122#p122](http://forum.phillw.net/viewtopic.php?f=18&t=96&p=122#p122)

Hope it is of help,

Regards,

Phill.

---

### Post by Slates on 2010-07-30
Hmmm. That didnt help Im afraid. I think there is something more fundamental wrong here.

To install Samba on Lucid is it right to do 

sudo apt-get install samba

and then expect to see a file in /etc/init.d/samba so I can issue the command

/etc/init.d/samba restart ?

I dont think even that is right, unless it's changed. Im sure that's wat I did for 9.10.

---

### Post by Morbius1 on 2010-07-30
Let me answer the only easy question you have:
> So I jump to the command line and try sudo /etc/init.d/samba restart but  get command not found. That’s how I restarted Samba on 9.1 – but now  something is wrong ?Does Samba now work differently, or has my memory  failed me ?Your memory has not failed you it's just not going back far enough. 10.04 changed how and where samba starts. 

First, the "samba" service no longer exists. Ubuntu has gone back to the beginning and separated the samba service into it's component daemons: smbd and nmbd.

So to restart "samba" you now need to issue the following:
```
sudo service smbd restart
```It get's more complicated however if samba is not running in the first place. Before if samba was not running and you did a "restart" it would start it - but not any more.

So to start the samba if it is not running you need to do a :
```
sudo service smbd start
```

---

### Post by Slates on 2010-08-06
OK, well thankyou for the info. 

It seems Im getting nowhere, and Idont know why. Its not like Im a complete newby, I had samba running just fine on 9.10.

So, I have the samba package installed, as youd expect (sudo apt-get install samba = already up to date).

I can suso service smbd start just fine. ps -ef | grep smbd reveals smbd is running just fine.

Ive cut down to a basic smb.conf file in /etc/samba.

I know my windows workgroup name and I have it right in smb.conf.

My other PCs in my wndows network can ping my Ubuntu machine.

Yet, no PC in my windows network can see my Ubuntu machine any more (so, explorer, MS network shows no clue of the Ubuntu machine).

Yet my Ubuntu machine can see the windows shared directories on my other machines.

None of the logs in /var/samba have been updated to the time Ive restarted smbd. 

It cant be that hard ! It wasnt this hard on 9.10....  

Here's my smb.conf file :

# NetBIOS name resolution options
   netbios name = D600
   server string = Ubuntu
   workgroup = Homework
   wins support = yes
# Master browser options (related to name resolution)
   local master = yes
   domain master = yes
   preferred master = yes
# Network security options
   hosts allow = 192.168.1.0/24
   interfaces = 127.0.0.1/8 192.168.1.0/24
# User security options
   security = user
   encrypt passwords = yes
   obey pam restrictions = yes
   username map = /etc/samba/smbusers  # Only useful if mapping usernames
   passwd program = /usr/bin/passwd '%u'
   passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n

[homes]
   comment = Home Directories
   read only = no

***Can anyeone please point to where I canlook or what I can change or try here ?***

---

