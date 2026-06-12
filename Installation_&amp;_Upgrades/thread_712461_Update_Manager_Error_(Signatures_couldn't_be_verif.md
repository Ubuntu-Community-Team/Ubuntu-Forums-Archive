---
title: "Update Manager Error (Signatures couldn't be verified)"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by newagelink on 2008-03-01
I've received an error similar to the one found [here]("http://ubuntuforums.org/showthread.php?t=523269") ...
> W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181
 [COLOR="Indigo"]... 'cept it doesn't involve medibuntu, like that other thread does.

What's going on? I'm attempting to upgrade as I've been told to by [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading). Another problem I have is that it's no longer telling me that a new distribution release is available, I suppose because I checked some option telling it not to tell me. :(

What do I do to fix it, and what does that error mean? I've burned the 7.10 release to a CD-R, but that website says I should upgrade through the Update Manager instead.[/COLOR]

---

### Post by fultona on 2008-03-01
[SIZE="3"]I'm a newbie to all this, but ... since I was getting the same error message as you were, I share with you what I've done.  

I went to [http://www.debian-multimedia.org/faq.php#q1](http://www.debian-multimedia.org/faq.php#q1) and found this error message there on the FAQ.  I followed the directions, did the download, etc., and I don't get the error message any more.

That said, it didn't solve my bigger problem.  

I was getting the error message whenever I was using my Update Manager.  I was following the directions at [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades) to do what it called "Network upgrade for Ubuntu desktops."  (Every time I ran the Update Manager, I got the error message above.)   Now that I've "fixed" the NO_PUBKEY error, however, the Update Manager still doesn't show me the availability of Gutsy.[/SIZE][/SIZE]

---

### Post by newagelink on 2008-03-01
[COLOR="Indigo"]fultona, thanks for the reply. Interesting debian link, but the "pubkey" it lists in that FAQ is different from my own, so I doubt doing what it says will help; I suppose it's a similar issue, though, that I'm missing some keyring package (as that answer says.)

Hum. I guess we'll both keep searching the Ubuntu forums. Frustrating![/COLOR]

---

### Post by zvacet on 2008-03-02
Type in terminal 

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 3E231AC7F4ECF181
gpg --export --armor 3E231AC7F4ECF181 | sudo apt-key add -

---

### Post by newagelink on 2008-03-02
Ugh! Thank you for the reply, but I'm having other problems it seems I must resolve first: > daniel@daniel-laptop:~$ gpg --keyserver hkp://subkeys.pgp.net --recv-keys 3E231AC7F4ECF181
gpg: fatal: can't create directory `/home/daniel/.gnupg': No space left on device
secmem usage: 0/0 bytes in 0/0 blocks of pool 0/32768
See [http://ubuntuforums.org/showthread.php?p=4440062#post4440062](http://ubuntuforums.org/showthread.php?p=4440062#post4440062) ... I just moved my home folder to another partition, but now I am out of space. :(

---

### Post by zvacet on 2008-03-02
What kind of files and data you have in home?If these are audio or video files why don´t you copy them on CD/DVD and delete from home?You can use this commands to make more space 

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```

---

### Post by newagelink on 2008-03-02
I freed up a few hundred MB of space. Now I get the following:
```
daniel@daniel-laptop:~$ gpg --keyserver hkp://subkeys.pgp.net --recv-keys 3E231AC7F4ECF181
gpg: directory `/home/daniel/.gnupg' created
gpg: can't open `/gnupg/options.skel': No such file or directory
gpg: keyring `/home/daniel/.gnupg/secring.gpg' created
gpg: keyring `/home/daniel/.gnupg/pubring.gpg' created
gpg: requesting key F4ECF181 from hkp server subkeys.pgp.net
gpg: /home/daniel/.gnupg/trustdb.gpg: trustdb created
gpg: key F4ECF181: public key "Aren Olson <reacocard@gmail.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
daniel@daniel-laptop:~$ gpg --export --armor 3E231AC7F4ECF181 | sudo apt-key add -
Password:
OK
```[COLOR="Indigo"]I entered my own sudo password when it asked that, and it gave me the response "OK". Did everything work correctly? (Thanks!) I just ran the Update Manager again, and now it's not giving me any errors, but it's also not showing the 7.10 update as being available. What do I do now? Should I used the 7.10 disc that I burned a while back?[/COLOR]

Edit: Had conversations in #ubuntu and #ubuntu-offtopic, which led to the following: > <ethereality> skarface: i have no clue about a "upgrade-manager -c" command
 rencore__: thanks, i will
--- rencore__ is now known as rencore_
<skarface> alt-f2 gksudo update-manager -d
<toros> There are only problems with the upgrade, when you used 3rd party repositories, or apps like envy or automatix
<_emet_> toros, yah I only use medibuntu
<ethereality> i love you guys so much
<Palomides> awwww

---

### Post by zvacet on 2008-03-03
```
sudo apt-get update && sudo apt-get upgrade
```

And yes you missed third party repo key.

---

### Post by kellemes on 2008-03-03
What's the point of creating a poll about this?!

---

