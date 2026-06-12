---
title: "Upgraded to Ubuntu 18.10 - Cannot share folder with windows"
date: 2019-01-18
forum: Installation &amp; Upgrades
---

### Post by linux.girl on 2019-01-18
Hi everyone,

After a long time without a working computer due to a botched upgrade from ubuntu TLS 14 to TLS 18, I finally gave up and re-installed everything from scratch.

Now I am in Ubuntu 18.10 and so many things are not working - I am trying to figure it out by myself - but it is not easy and I am sorry if I come here every now and then when I reach a dead end.

I will go methodically issue by issue.

So issue number one is that I always shared files and folders and external drives from my Ubuntu to my Windows 10. Now it is no longer working. I get the following error even BEFORE I enter the password:

(I know the dots are there, it is just the timing of the screenshot).

I have smb.conf configured correctly, I tried even to use [COLOR=#242729][FONT=Arial]system-config-samba but to no availe - still asks me for a user and pass. I didn't configure it to ask for a user and pass, but even if I did, I give the correct ones and it still doesn't accept.

[/FONT][/COLOR]I also got this error, every time is something different:



 
 

Any ideas? Thanks!

---

### Post by Morbius1 on 2019-01-18
Without knowing how you are configured I offer three possible guesses:

[1] It's not a samba issue it's a Linux permissions issue.

Something that you can un-do quick enough is to make the client to this system look like you - at least for your samba shares. You do that by:

Editing /etc/samba/smb.conf and adding a line right under the workgroup = WORKGROUP line:
```
force user = linux.girl
```
[COLOR=#000080][I]Change linux.girl to your Ubuntu login user name

[/I][/COLOR]Then restart smbd:
```
sudo service smbd restart
```

[2] If this is supposed to be a guest accessible share remove any entries you made to create a samba password for the client. 

I suspect that is why you are now getting the "more than one username ... " error. 

[3] Something is really messed up with your configuration and I can only determine that is I see how you are configured. 

Posing the output of these commands should do it:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by linux.girl on 2019-01-20
Hi, thank you SO much! Please see my answer attached.

---

### Post by Morbius1 on 2019-01-20
[1] Not sure why this happened since it's not something one does on purpose but you have the wrong setting on one item:
> encrypt passwords = No
Edit /etc/samba/smb.conf and change that to Yes:
> encrypt passwords = [COLOR=#000080]**Yes**[/COLOR]
Then restart smbd:
```
sudo service smbd restart
```
[2] You have shared the target folder 2 different ways.

Once in smb.conf:
> [MyBook4]
    path = /media/myuser/MyBook4
    writeable = yes
    browseable = yes
    valid users = myuser
    ntlm auth = true
And again in your file manager ( usershare ):
> [MyBook4]
path=/media/myuser/MyBook4
comment=
usershare_acl=Everyone:F,
guest_ok=n
It's generally a bad idea to use both methods at the same time on the same folder and technically they don't match. THe one in smb.conf allows only you. The one you created in Nautilus allows anyone with the right credentials. I would choose one or the other.

[3] With the "force user = myuser" added you fixed the problem created by the /media/myuser folder so if you really want this to be a guest accessible share you can go back to Nautilus and set it to allow guests if you want. Just make sure you remove the share from smb.conf.

As for your other questions in the text I suggest opening a different topic in the forum for them so you attract a wider audience.

---

### Post by linux.girl on 2019-01-21
Thank you so much!! What do you think I should choose? Share via Samba or Nautilus?

---

### Post by Morbius1 on 2019-01-21
They are both samba just different ways to create share definitions. 

If this is just a normal home network where user1 wants to share some stuff with user2 on the network creating shares in Nautilus + the "force user" you are using should be enough.

But it really makes no difference to samba.

---

