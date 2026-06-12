---
title: "Should I encrypt my home directory under this situation?"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by zhaotianwu on 2010-11-18
I have already encrypt the whole root using LUKS by dm-crpyt during my Alternate CD installation. At almost the end of the installation I was prompt to create passphrase for my user's account and had the option to "configure your home directory for encryption...".
Is it still helpful, in any ways, that I create a strong passphrase for my user's account and encryption the home directory, after all the partition was encrypted LVM? Can anybody help analyze the benefit of this? Thanks.

---

### Post by Herman on 2010-11-18
Ubuntu is secure by default, but if you install software from unknown sources or services which open ports, file system encryption probably won't protect you.
Crackers on your local network or the internet will be  using the same kernel you're using to access your files if they can get in. In that kind of scenario a strong user account password could maybe give you some extra protection, especially if you remember to change the file permissions for your /home/username folder too.
 
File system encryption can protect your information from unauthorized   access by somebody who might steal your laptop or somebody who might go   into your office while you're out and boot your computer with a Live CD   to snoop through your files to steal your business or personal  information. 

If you just have an encrypted /home folder (or partition), you will have an operating system that's not too hard to fix if something goes wrong with it, and your personal data will be protected much better than a standard installation. 
If something bad happens though, and you don't have your data backed up, or if your most recent backup is very far out of date then you will have a slightly harder job to recover your data. 
You should plan ahead about how you might do that if you ever need to and possibly do a trial run at some time beforehand, something like a fire drill.
Make sure you know how to decrypt your /home from a Live CD and rescue your data.

If you have the entire / (root) encrypted, it can give a little more security than just an encrypted /home, but it also makes things a little more complicated if you need to run a file system check or chroot into the operating system to fix something. 
You'll need to install some extra software in your Live CD or USB-installed Ubuntu and go though a couple of extra steps more than most people with ordinary installations. 
It's not difficult, but it does mean you have more procedures to go through than most people.

If you have both your / (root) encrypted as well as your /home, your /home will be double encrypted, so you will also need to be prepared to go through twice as many hoops if some kind of accident or disaster occurs and you need to fix your operating system or rescue files. Remember, the goal of security is to try to make things hard if not impossible for the cracker, while still keeping things reasonably convenient for the authorized users.

If you make regular backups so rescuing data will never be an issue, remember of course you'll need to secure the media you keep your backups in. It's no use having double or even triple encrypted data in your computer is someone can simply pick up your non-encrypted backup DVD or USB and make off with it.

Another thing to be aware of is, encryption creates a little drag on  performance, or at least it seems so to me. It's not a big drag, and  with just one lot of encryption you probably won't notice it much.  Having encryption on top of more encryption though, might start to slow  your system down a little more noticeably.

Personally, in my opinion it's not necessary to have two layers of encryption. If you have something very important though, and you'll sleep better at night knowing it's double encrypted, it possibly it might be worth doing.

If you haven't already done so, I recommend thoughly reading the following link, I think you'll probably like it, [B][Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812") - by bodhi.zazen

[/B]

---

### Post by zhaotianwu on 2010-11-18
> **Herman said:**
> Ubuntu is secure by default, but if you install software from unknown sources or services which open ports, file system encryption probably won't protect you.
Crackers on your local network or the internet will be  using the same kernel you're using to access your files if they can get in. In that kind of scenario a strong user account password could maybe give you some extra protection, especially if you remember to change the file permissions for your /home/username folder too.
 
File system encryption can protect your information from unauthorized   access by somebody who might steal your laptop or somebody who might go   into your office while you're out and boot your computer with a Live CD   to snoop through your files to steal your business or personal  information. 

If you just have an encrypted /home folder (or partition), you will have an operating system that's not too hard to fix if something goes wrong with it, and your personal data will be protected much better than a standard installation. 
If something bad happens though, and you don't have your data backed up, or if your most recent backup is very far out of date then you will have a slightly harder job to recover your data. 
You should plan ahead about how you might do that if you ever need to and possibly do a trial run at some time beforehand, something like a fire drill.
Make sure you know how to decrypt your /home from a Live CD and rescue your data.

If you have the entire / (root) encrypted, it can give a little more security than just an encrypted /home, but it also makes things a little more complicated if you need to run a file system check or chroot into the operating system to fix something. 
You'll need to install some extra software in your Live CD or USB-installed Ubuntu and go though a couple of extra steps more than most people with ordinary installations. 
It's not difficult, but it does mean you have more procedures to go through than most people.

If you have both your / (root) encrypted as well as your /home, your /home will be double encrypted, so you will also need to be prepared to go through twice as many hoops if some kind of accident or disaster occurs and you need to fix your operating system or rescue files. Remember, the goal of security is to try to make things hard if not impossible for the cracker, while still keeping things reasonably convenient for the authorized users.

If you make regular backups so rescuing data will never be an issue, remember of course you'll need to secure the media you keep your backups in. It's no use having double or even triple encrypted data in your computer is someone can simply pick up your non-encrypted backup DVD or USB and make off with it.

Another thing to be aware of is, encryption creates a little drag on  performance, or at least it seems so to me. It's not a big drag, and  with just one lot of encryption you probably won't notice it much.  Having encryption on top of more encryption though, might start to slow  your system down a little more noticeably.

Personally, in my opinion it's not necessary to have two layers of encryption. If you have something very important though, and you'll sleep better at night knowing it's double encrypted, it possibly it might be worth doing.

If you haven't already done so, I recommend thoughly reading the following link, I think you'll probably like it, [B][Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812") - by bodhi.zazen

[/B]

  Hi Herman, thank you for this guide, it is very much helpful! I have two questions though:  1) Is there any disadvantage/risk to have exactly the same passphrase for the encrypted LVM and the user's account? After reading your tips above, it seems to me that they are equally important.(one is for online-threat, while the other is for someone who can access when the computer is off)   2) How to change the file permissions for my /home/username folder? Do I have to go though each folder one by one or is there some way more efficient? Could you please provide a link to this?   Many thanks!  By the ways, I'm the only user on my computer.

---

### Post by Herman on 2010-11-19
> 1) Is there any disadvantage/risk to have exactly the same passphrase for the encrypted LVM and the user's account? After reading your tips above, it seems to me that they are equally important.(one is for online-threat, while the other is for someone who can access when the computer is off)
It seems like you need a username and password for almost everything these days.
You should use a different password or pin number for everything you need a password or pin number for. 
It would be easy to just remember one password and use the same password for everything, and it's a well known fact that a lot of people do that. The problem is, there could be some instances when you are asked for a password and the organization you're giving it to doesn't have good security or a person working there is not trustworthy. In that case that person could potentially gain access to all your accounts and might even ultimately be able to steal your identity!
I have read that there are some crackers with websites offering some kind of bait or reward like a free download of some kind or another which require setting up a user account and password. They're really only there for the purpose of collecting people's usernames and passwords, because crackers know that most people are lazy.
I don't think installing Ubuntu with the same password for the user account and the LUKS file system encryption will matter all that much in itself, but be aware that it's a bad habit to use the same password more than once or twice.

[GPass]("http://projects.netlab.jp/gpass/") is a good program for keeping track of lots of different user accounts and passwords in Ubuntu.

Besides, as long as you stick to the official Ubuntu repositories and you don't install services which open ports you should be fine. If you really must install services, install another Ubuntu and don't keep any personal information in it and use that installation for running services.

---

### Post by Herman on 2010-11-19
> 2) How to change the file permissions for my /home/username folder? Do I  have to go though each folder one by one or is there some way more  efficient? Could you please provide a link to this?   It's in the link I already provided,  **[Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812") - by bodhi.zazen**, look about half way down the page.
```
sudo chmod 700 $HOME
```

---

### Post by zhaotianwu on 2010-11-19
> **Herman said:**
> It's in the link I already provided,  **[Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812") - by bodhi.zazen**, look about half way down the page.
```
sudo chmod 700 $HOME
```

  Hi, Herman, should it be "sudo chmod 700 /HOME", instead of "sudo chmod 700 $HOME"? Was it a typo in your last post?  Will this also apply to partition using the whole free space as root and no separate /home directory?

By the way, the "Ubuntu Security" post you mentioned doesn't tell anything about permission other than permissions relating to running WINE. And I've searched online that tells a lot about the drawbacks of using this command line, such as being locked into failsafe terminal etc. Could you explain a bit about this permission technique in this thread so it will become a valuable entry for many beginners? Thanks.

---

### Post by Herman on 2010-11-19
:D There's no typo, it's 'sudo chmod 700 $HOME' , I'll get around to explaining that in a while ...

... and yes. it applies to installations with the entire operating system in one integral / partition, which has always been my favorite except in my 4GB EeePC, where I was forced to make a separate /home in an SD card due to the small size of the SSD.

In the meantime, here's an example of the output from 'ls -l /home' in a computer with a freshly installed Ubuntu installation,
```
herman@herman-Aspire-T310:~$ ls -l /home/
total 4
[COLOR=Red]**drwxr-xr-x**[/COLOR] 30 herman herman 4096 2010-11-20 07:31 herman
```Compare that with the result from the same command from my main working Ubuntu operating system, which has had the command 'sudo chmod 700 $HOME' run on it,
```
herman@amd-quad-lynx:~$ ls -l /home/
total 124
[COLOR=Red]**drwx------**[/COLOR] 71 herman herman 122880 2010-11-20 05:34 herman
```The characters I have shown in red, (above) represent the permissions for my /home/<username>, or in my case, /home/herman directory.
The '[COLOR=Red]**d**[/COLOR]' at the beginning indicates it's a directory, if it was just a file it would start with a dash instead.

The next three characters, '[COLOR=Red]**rwx**[/COLOR]' apply to me, the owner, and let me 'read', 'write', and 'execute' my files.

The fourth, fifth and sixth characters apply to any groups I may have registered in 'System', 'Adminstration', 'Users and Groups', in my Ubuntu operating system.
Running the aforementioned command has changed the permissions for 'groups' from '[COLOR=Red]**r-x**[/COLOR]' to '[COLOR=Red]**---**[/COLOR]'.
Members of groups I have registered are now no longer able to (easily) see inside my /home/username directory. 

The last three characters refer to the file permissions for 'anyone', and I have changed the permissions for 'anyone' to from '[COLOR=Red]**r-x**[/COLOR]' to '[COLOR=Red]**---**[/COLOR]'.
Anyone is now no longer able to (easily) see inside my /home/username directory. 

Linux file permissions aren't the be all and end all of security in Linux, but they're a good start and it's a very interesting subject to read about and experiment with for yourself.
If you're interested see [FilePermissions]("https://help.ubuntu.com/community/FilePermissions") - Understanding and using file permissions - Ubuntu Community Docs.
    Tuxfiles has a great page on how to use the chmod command, [_Linux File Permissions_]("http://www.tuxfiles.org/linuxhelp/filepermissions.html")
   Tuxfiles has another great page on how to use the chown command too, [How to change a file's owner and group in Linux - 1.0]("http://www.tuxfiles.org/linuxhelp/fileowner.html")

   In practical use, if there are a number of people sharing the same computer with a Ubuntu operating system in it, each user can have their own user account.
It could be a husband and wife or even a whole family, or it could be a work computer and be shared by several co-workers.
If you don't care if others can see your files and you just want to share everything , it's okay to leave your /home/username file permissions alone.
If you want to have some privacy you can set file permissions to restrict the access for polite family members and friends. 
File permissions are like a lock for keeping out 'honest theives', most people are too polite to cut a padlock, and file system permissions rely on people not bothering to boot a live cd and use a sudo command to see inside your private files. These people have physical access to the computer so they can do that. This is what file encryption is good for.

Another practical scenario is if you have ssh networking set up in a private LAN and you have a number of PCs networked together.
This is another kind of setup that might be fun in the home, and useful in a workplace.
It's bad to let anyone log in by ssh as root. In each PC, a user account can be set up for the owner of each of the other PCs in the network. 
That means everyone can ssh into their own user account in any of the other PCs in the LAN.
This is where the 'groups' thing really starts to get handy, especially if it's a large LAN.
In this case, people may not necessarily have physical access to other's machines.
A more common and probably better setup would be to have just one central server.

Ssh networking can be set up to work over the WAN (internet) as well, but more advanced networking security knowledge would be recommended compared with what's needed within a LAN which is protected by a firewalled router. A better idea if you want to be able to collaborate with someone on a project or share files would be to use Ubuntu One instead. 

Installing 'services', (networking software), which open ports is the opposite of security. 
Consider having two separate Ubuntu installations, one for ultra security and the other for networking and sharing.

---

### Post by zhaotianwu on 2010-11-19
> **Herman said:**
> :D Okay, here's an example of the output from 'ls -l /home' in a computer with a freshly installed Ubuntu installation,
```
herman@herman-Aspire-T310:~$ ls -l /home/
total 4
[COLOR=Red]**drwxr-xr-x**[/COLOR] 30 herman herman 4096 2010-11-20 07:31 herman
```Compare that with the result from the same command from my main working Ubuntu operating system, which has had the command 'sudo chmod 700 $HOME' run on it,
```
herman@amd-quad-lynx:~$ ls -l /home/
total 124
[COLOR=Red]**drwx------**[/COLOR] 71 herman herman 122880 2010-11-20 05:34 herman
```


So what does this "[COLOR=Red]**drwxr-xr-x**[/COLOR]" and "[COLOR=Red]**drwx------**[/COLOR]" implicate?:confused:

---

### Post by Herman on 2010-11-19
> So what does this "[COLOR=Red]**drwxr-xr-x**[/COLOR]" and "[COLOR=Red]**drwx------**[/COLOR]" implicate?:confused:Sorry, but this is quite a complicated subject to try to explain, I'll need to keep on working on it. :)

Quoted from [_Linux File Permissions_]("http://www.tuxfiles.org/linuxhelp/filepermissions.html") - tuxfiles, (but re-arranged a little),

> **On a regular  file, **
the read permission bit means the file can be opened and read. 
the write permission means you can modify the file, aka write new data to the  file. 
the execute permission means you can execute the file as a program or a  shell script. 


**On a  directory,**
the read permission means you can list the contents of the  directory.
         the write permission means you can  add, remove, and rename files in the directory. This means that if a  file has the write permission bit, you are allowed to modify the file's  contents, but you're allowed to rename or delete the file only if the  permissions of the file's *directory* allow you to do so.
the execute permission (also called the "search bit") allows you to access files in the directory and enter it, with the cd  command, for example. However, note that although the execute bit lets  you enter the directory, you're not allowed to list its contents, unless  you also have the read permissions to that directory.


---

### Post by Herman on 2010-11-19
> Hi, Herman, should it be "sudo chmod 700 /HOME", instead of "sudo chmod 700 $HOME"? Was it a typo in your last post?In mathematics, you might learn that a + b = c, where 'a', 'b', and 'c' are variables, they can represent *any* (number).
The word '$HOME is something like that in Linux, but different, it is called a 'system variable'. 
In this case the word $HOME is the same as typing '/home/herman' for me, and for you it would be the same as typing '/home/zhaotianwu', except I'm not really sure your username in your computer really is zhaotianwu. It might be or it might not be, that's your username for Ubuntu Web Forums, but there's no guarantee that's also your username inside your operating system. It's easier to just say $HOME instead.

See [Variables in shell]("http://www.freeos.com/guides/lsst/ch02sec02.html") -  Linux Shell Scripting Tutorial v1.05r3 A Beginner's handbook

Actually, I got that command from **[Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812") - by bodhi.zazen. **When bodhi.zazen included that command in his Ubuntu Security tutorial, he didn't know who would be reading it, so he used the system variable $HOME because then anybody can copy that command and use it even if they aren't really sure what they're doing. :)

---

### Post by zhaotianwu on 2010-11-20
> **Herman said:**
> In mathematics, you might learn that a + b = c, where 'a', 'b', and 'c' are variables, they can represent *any* (number).
The word '$HOME is something like that in Linux, but different, it is called a 'system variable'. 
In this case the word $HOME is the same as typing '/home/herman' for me, and for you it would be the same as typing '/home/zhaotianwu', except I'm not really sure your username in your computer really is zhaotianwu. It might be or it might not be, that's your username for Ubuntu Web Forums, but there's no guarantee that's also your username inside your operating system. It's easier to just say $HOME instead.

See [Variables in shell]("http://www.freeos.com/guides/lsst/ch02sec02.html") -  Linux Shell Scripting Tutorial v1.05r3 A Beginner's handbook

Actually, I got that command from **[Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812") - by bodhi.zazen. **When bodhi.zazen included that command in his Ubuntu Security tutorial, he didn't know who would be reading it, so he used the system variable $HOME because then anybody can copy that command and use it even if they aren't really sure what they're doing. :)


Thanks Herman. I have another question, from a security point of view, to what extent can I trust the downloads from the Universe repository?Should I ban it altogether if I really want a secure environment?

---

### Post by Herman on 2010-11-20
Packages from the Universe Repository are not necessarily checked and monitored by Canonical and may not receive security updates as promptly as software from the main repository. 

Once again, it's a matter for the individual to decide, depending on the level of security needed verses the functionality you want to have from your operating system and installed programs. 

For me personally, it's very important to have the use of some of the programs from Universe and I think the risk of a program from the Universe repository having a security flaw in it that could affect me is negligible. The Universe Repository is huge and some of my favorite programs come from Universe.  I only have a few installed right now, but there are a great number that I have used in times past and it's nice to know they're available for installation whenever decide I need them.

Some of the best security related software is available from the Universe repository too. Read this link, it's a couple of years old and it's five pages long but it's definitely worth the time taken to read, [Paranoid Penguin - Security Features in Ubuntu]("http://www.linuxjournal.com/article/9972") - Linux Journal. 
Note the security software from Universe listed in table 3 on page 3.
Also, note the information about the author at the bottom of page 4. :)

Once again though, if lives depended on it and I really needed hyper security, I'd dual boot with two Ubuntu installations, a hyper secure one and one for general purpose use.  After all, Ubuntu is free and not restricted by a licence that says we can only have one installation in one PC, we can install Ubuntu as many times as we like.

---

### Post by zhaotianwu on 2010-11-21
> **Herman said:**
> Packages from the Universe Repository are not necessarily checked and monitored by Canonical and may not receive security updates as promptly as software from the main repository. 

Once again, it's a matter for the individual to decide, depending on the level of security needed verses the functionality you want to have from your operating system and installed programs. 

For me personally, it's very important to have the use of some of the programs from Universe and I think the risk of a program from the Universe repository having a security flaw in it that could affect me is negligible. The Universe Repository is huge and some of my favorite programs come from Universe.  I only have a few installed right now, but there are a great number that I have used in times past and it's nice to know they're available for installation whenever decide I need them.

Some of the best security related software is available from the Universe repository too. Read this link, it's a couple of years old and it's five pages long but it's definitely worth the time taken to read, [Paranoid Penguin - Security Features in Ubuntu]("http://www.linuxjournal.com/article/9972") - Linux Journal. 
Note the security software from Universe listed in table 3 on page 3.
Also, note the information about the author at the bottom of page 4. :)

Once again though, if lives depended on it and I really needed hyper security, I'd dual boot with two Ubuntu installations, a hyper secure one and one for general purpose use.  After all, Ubuntu is free and not restricted by a licence that says we can only have one installation in one PC, we can install Ubuntu as many times as we like.

   If in the installation I banned Universe repository, can I at a later point switch on it without affecting the overall functionality? I mean, is there anything in the installation process that must come from the Universe, and no matter how you switch it on or off later it wouldn't work if the initial installation didn't allow Universe? In particular, what do you think of a password management software called keepassx?

---

### Post by Herman on 2010-11-21
> If in the installation I banned Universe repository, can I at a later  point switch on it without affecting the overall functionality? I mean,  is there anything in the installation process that must come from the  Universe, and no matter how you switch it on or off later it wouldn't  work if the initial installation didn't allow Universe? I don't imagine anything from the Universe Repository would have been required at installation time, and no, I don't think it will do any harm at all to enable the Universe Repository at any time you like.
 > In particular, what do you think of a password management software called keepassx?     I highly recommend the use some kind of password manager, and if you think you'll like KeePassX, then I think you should go ahead and try it out. I have tried it but it was a while ago. I had already been using GPass prior to that and I remember having a hard time deciding which one of the two to keep using. GPass turned out to be my personal preference but I can't remember why, possibly only because of familiarity since it's the one I started with. KeePassX has more features.

---

### Post by Herman on 2010-11-21
KeePassX is a free/open source software and like other free/open source  software, if you want to be particularly careful and you don't mind  doing a little more work, you can get the source code and compile it  yourself. The fact that the source code is available for inspection is  one of the reasons why open source software is a sensible choice over  proprietary software from a security point of view.  

Did I say a 'sensible choice'?
It's the *only* choice if you care about security.
Installing software that comes in binary only format and whose contents  are kept secret is something like carrying a locked briefcase that  you're not allowed to look at the contents of.  If a stranger asked you  to carry such an item would you take it? I wouldn't.
Yet millions of people all over the world have come to accept  proprietary software and even the habit of installing binary programs  from unknown sources with hardly a second thought. Clearly most of the  world's population is either ignorant or crazy.

---

### Post by zhaotianwu on 2010-11-21
> **Herman said:**
> KeePassX is a free/open source software and like other free/open source  software, if you want to be particularly careful and you don't mind  doing a little more work, you can get the source code and compile it  yourself. The fact that the source code is available for inspection is  one of the reasons why open source software is a sensible choice over  proprietary software from a security point of view.  

Did I say a 'sensible choice'?
It's the *only* choice if you care about security.
Installing software that comes in binary only format and whose contents  are kept secret is something like carrying a locked briefcase that  you're not allowed to look at the contents of.  If a stranger asked you  to carry such an item would you take it? I wouldn't.
Yet millions of people all over the world have come to accept  proprietary software and even the habit of installing binary programs  from unknown sources with hardly a second thought. Clearly most of the  world's population is either ignorant or crazy.


I promise this would be my last question or it could be off the topic too much.
Some web browsers can automatically store the username and password (e.g. IE, firefox, etc.), and some of them are so convenient. However, from a security perspective, is it recommended not to store your password with web browsers? Gpass vs. firefox, which one is more secure to remember your password?
 By the way, you are so great, Herman!:P

---

### Post by Herman on 2010-11-22
In your case since you have an encrypted file system it wouldn't matter. 

I usually do both, I let Firefox remember my passwords for the convenience of it and I keep a copy of all my passwords in .gpass as well. 
I use .gpass for my long term password storage. I have kept the same .gpass through backups and added more accounts and passwords to it over many Ubuntu installations. I usually have a new firefox when a new version of Ubuntu comes out and I like to start fresh with it and just add what I need.

The time when people should be particularly careful not to let a web  browser remember any password would be when they are traveling and using  a public computer such as in an internet cafe. I think most people know that. 

Whenever a person has an operating system installed in a USB flash  memory stick or a laptop it's more important to have a good strong user  password and probably an encrypted file system or at least an encrypted  /home folder. 
A USB flash memory stick can very easily be lost or stolen  and laptops get lost or stolen too. Then if the thieves or a dishonest finder can boot the operating system and get into the user account they would have access to any sites on the internet the stored passwords are good for. Even with a good strong user password you should be fairly safe though, Ubuntu's passwords actually work and Ubuntu's Firefox cookies are not just stored as plain text files. They won't be able to mount the file system and just copy the cookies out. With a fully encrypted / you should be perfectly safe as far as stored passwords in firefox passwords go. :)

I'm enjoying helping you because you ask excellent questions and that helps me to learn more too. Often I need to look up things I to check and confirm my opinions in order to try to give a good answer. Thanks for your great questions. :)

---

