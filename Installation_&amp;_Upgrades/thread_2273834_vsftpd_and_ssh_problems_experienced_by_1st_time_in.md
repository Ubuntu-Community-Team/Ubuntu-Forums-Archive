---
title: "vsftpd and ssh problems experienced by 1st time installer. aka: Help?"
date: 2015-04-16
forum: Installation &amp; Upgrades
---

### Post by kallen2 on 2015-04-16
Not sure where to turn, so I'm posting here.

I've got Ubuntu server 14.04 operating, and i've been trying to figure out how to use Filezilla to access my server box from my laptop.  I have got Putty setup to open a terminal window and operate with a key, but I've spent the majority of my day trying to get this ftp client to connect securely to the server to no avail.  I've read a pile of different sites and learning more which is great, but I've found no success with getting the ftp service rolling.

I am still confused by the terminology as to how the ssh keys work.  Many sites say to create the private key on the system i'm connecting with, but does not the server itself require the private key to verify the public key? if so, why am i storing the private key on the machine that will be used to access in remotely, as well, why would I want to give the private key to any remote user if it's supposed to be private?  I've gone in and installed ssh as well, but not sure if this is used for a separate service from vsftpd, I've created users and established home folders.  I've added user names to the sshd.conf.  still cannot connect.

The primary message I'm getting from Filezilla is Error:    Disconnected: No supported authentication methods available (server sent: publickey)   Error:    Could not connect to server.    So clearly I'm supposed to establish something with the keys, but I do not see how to do this listed on the sites and forums on the web.   

Thanks if you can provide some insight.

---

### Post by Lars Noodén on 2015-04-16
Welcome.

If you have SSH working, then there is no need to complicate and weaken things with [insecure, old FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).  The same package, openssh-server, that gives you SSH also gives you SFTP.  So you can remove vsftp and connect using SFTP with FileZilla or Nautilus.

About the key pairs, it does not so much matter where the keys are generated just that the private key is on the client and a copy of the public key gets to the server in the right place.  

Can you check using the terminal that you can connect with keys?  

```

ssh -i /home/kallen2/.ssh/some_key_rsa  kallen2@xx.yy.zz.aa

```

Substitute the path to the right private key and the ip address (or hostname) for the server, and of course the relevant user name.  

What versions of Ubuntu are you using on the client and the server?

---

### Post by grooup on 2015-04-16
[COLOR=#000000]Hi,[/COLOR]
[COLOR=#000000]I have lenovo z510 laptop and installed ubuntu 14.10 but when i open computer i am getting errors so that i am starting with recovery mode in grub.[/COLOR]
[COLOR=#000000]Then i see ata5.00 failed, failed fpdma queued, comreset faild status DRDY, ATA bus error.[/COLOR]
[COLOR=#000000]I am waiting your suggestions.[/COLOR]
[COLOR=#000000]Thank you.
_____________________
dolii[/COLOR]

---

### Post by kallen2 on 2015-04-18
Lars, Hey, sorry it took so long to get back to you.  (Grooup, wrong thread man).

Thing is, i'm trying to set up a file server I can access from anywhere and have select people access it.  So I'm trying to ftp in from a WIndows 7 laptop with no luck.  I can putty in, but that's it.  I just tried using my android tablet with no luck either, i simply cannot make a connection.  I've set up ftpd before in a win environment, but this vsftpd is throwing no help my way.  I can't see what it's doing and I've spent many hours trying to use filezilla to securely access the server.   Not sure what you mean by openssh. First thing i did was setup vsdtpd and then configured the conf file appropriately.  I set up 2 user accounts with home dirs, so in theory (i think) I should be able to access the server by using my dyndns service with port 22, and it should ask for my ssh key pwd like the putty window does (and that works)  but filezilla fails, as do the other less usable android apps. (vssh_ , filezilla, ftpcafe)

Not sure why this whole ssh key thing seems incredibly convoluted...

---

### Post by kallen2 on 2015-04-18
Filezilla offers SFTP SSH File Transfer Protocol  but no where asks where my key pairs are, so how can this even work?   To answer some of your other questions, the Server is Ubuntu 14.04.  I can connect with the key I set up for the terminal in Putty, it asks for my key pwd and it works, i can terminal in and move around the directories, create user, etc.   So I know the keys can work, but it simply fails on Filezilla's GUI windows app (and android apps I've tried with).  I try vssh on android and when i choose my private key (made with puttygen on the windows laptop and copied over by bluetooth and put into .ssh folder), it simply crashes every time.  There really has to be an easier way to make ssh work, this has been/still is a major headache

---

### Post by Lars Noodén on 2015-04-18
> **kallen2 said:**
> Filezilla offers SFTP SSH File Transfer Protocol  but no where asks where my key pairs are, so how can this even work?   To answer some of your other questions, the Server is Ubuntu 14.04.  I can connect with the key I set up for the terminal in Putty, it asks for my key pwd and it works, i can terminal in and move around the directories, create user, etc.   So I know the keys can work, but it simply fails on Filezilla's GUI windows app (and android apps I've tried with).  I try vssh on android and when i choose my private key (made with puttygen on the windows laptop and copied over by bluetooth and put into .ssh folder), it simply crashes every time.  There really has to be an easier way to make ssh work, this has been/still is a major headache

Ok.  If you can connect with the keys, then the keys are good.  If you load the keys in to the agent then FileZilla will find them as long as you have same desktop session.  I looked for a way to do this with Seahorse but couldn't find it.  On your desktop machine, press ctrl-alt-t to get a terminal then use [ssh-add](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh-add.1.html) to load the key into the agent.

```

ssh-add /home/kallen2/.ssh/some_key_rsa

```

It will then ask you for the key's passphrase and that will be it.  FileZilla will find the agent and use the key from there to connect.

You mention puttygen, I haven't used it and it has been a Very Long Time (r) since I've used PuTTY, but I get the idea that the keys made by puttygen are not quite the same:
  [http://stackoverflow.com/questions/2224066/how-to-convert-ssh-keypairs-generated-using-puttygenwindows-into-key-pairs-use](http://stackoverflow.com/questions/2224066/how-to-convert-ssh-keypairs-generated-using-puttygenwindows-into-key-pairs-use)

---

### Post by kallen2 on 2015-04-18
I load the pub key I moved over using your directions and i get  "WARNING: UNPROTECTED PRIVATE KEY FILE!"      At this point nothing is  working and have tried enough things to now not be sure how i got it to  work for putty but i can't get it functioning with Filezilla, nor  another key with putty.  I have to use PuttyGen on the windows machine,  unless there is another application that lets me do this? 

Here  is what i understand:  I have to make a key pair on my laptop here, put  the private key in the local laptop ssh folder and move the public key  to the server.  I can edit the authorized key file in .ssh on ubuntu  14.04 and enter the new key and save it. I've run nmap to verify ssh is  running, so now with the pub key in .ssh, i should just be able to log  in with filezilla with the ip and std port (22).  I should see the key  in 'Password & Keys' (Seahorse) but i only see the one key i first  made that lets me ssh in with Putty, but doesn't work with Filezilla  sftp. (? why not? ...) .  I initially made an etc/ssh folder and just  dropped the key files in there but that clearly didn't work, so i assume  I must import them into an operations file manually (cp paste, which  should then show up in passwords and Keys (but they do not).  I cannot  import with Passwords & Keys, i only get options to create more  keys...   It's funny to see videos saying you can set up ssh in 5  minutes.. this has taken me days and still no closer to getting it to  work.   

The Filezilla dialogue i'm getting is: 

Status:    Connecting to xxxxx.xxxxx.com...
Response:    fzSftp started, protocol_version=2
Command:    open "kxxxxxx@xxxxx.xxxxxxx.com" 22
Error:    Disconnected: No supported authentication methods available (server sent: publickey)
Error:    Could not connect to server 

This should (?) be grabbing the key from the .ssh authorized  keys and verifying that the remote connection (laptop) has the private  key that matches the public key on the server.  This simply isn't  working for me

---

### Post by steeldriver on 2015-04-18
If you're connecting from a windows box, you considered using Winscp in place of FileZilla? it integrates with PuTTY's pagent (key manager) and always works flawlessly for me.

---

### Post by kallen2 on 2015-04-18
Dude, Winscp worked immediately as you mentioned.  It let me grab the working ssh key i have and there it is.   Solved the first problem of getting a GUI file tool to securely port in.  I still cannot create/implement another working key though. 

 Been trying to connect my Android tablet. I create a key pair on my server and then copy the private one to my Android device and import it. When i attempt to connect i get "Trying to Authenticate. [Your host does not support 'password' or 'keyboard-interactive' authentication.]  It would seem I have to somehow add the public key to Seahorse/OpenSSH/Passwords&Keys  as I see the one working ssh key is listed there, but I find no option on how to import any new public keys.   Realistically, Filezilla and the andoid ssh connecting devices should work.. so something is broken on my server, but I'm not sure where to start.  SSH authentication with Ubuntu...  What i need to know is...  are the problems I'm experiencing due to not knowing how to integrate a public key into Ubuntu 14.04 server?  Because i can make keys, but i don't know if i'm failing to make them available to the software tools, or if the tools themselves aren't functioning well (or I'm just totally clueless about something important of which i am not aware yet)

---

