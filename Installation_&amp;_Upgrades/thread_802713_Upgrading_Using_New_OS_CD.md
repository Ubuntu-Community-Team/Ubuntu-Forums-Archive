---
title: "Upgrading Using New OS CD"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by Muchohombre57 on 2008-05-21
I am trying to upgrade from 7.04 to 8.02 using the CD which I received in the mail yesterday. From what I have read after getting to the 7.04 desktop you insert the 8.02 Cd and a window pops up asking you if you would like to upgrade using the CD. I get no upgrade window. My Ubuntu computer is not online right now so I would like to be able to use the new CD.

Thanks to all in advance!

---

### Post by Pumalite on 2008-05-21
7.04>7.10>8.04
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by stephenb on 2008-05-21
I've done that upgrade but sometimes regret it because things are broken in Hardy, at least for me. It has been a little disappointing. 

You can see some of the problems I've got here: [http://ubuntuforums.org/showthread.php?t=800978](http://ubuntuforums.org/showthread.php?t=800978)

However, I think in time many of the issues I listed should be solved, hopefully. 

I found the upgrade by CD a bit bugging. I was connected to the Internet and perhaps because of that it refused to upgrade from CD only, as I had nominated it to do (so it would be quicker). I think it got over a third of the packages from the CD and the rest from the Net. 

If the upgrade dialog doesn't appear, you could try this command:

gksu sh /cdrom/cdromupgrade

Be aware that you will need to have the alternate or server CD for this to work. Also, as stated by Pumalite, you must upgrade to Gutsy first and then to Hardy.

---

### Post by Muchohombre57 on 2008-05-21
Stephenb:

Thank you for your response! I have used that command. A window pops up. I click on "Run in terminal." Another window opens up asking me for my password. I enter it and click on "OK." The window then disappears. Then nothing else happens.

I also tried this by clicking on "Run with file", but being new to Ubuntu I get lost. I believe it asks me what to open it with?

Thank you!

---

### Post by Muchohombre57 on 2008-05-21
I forgot. I do have the latest version of Ubuntu. The desktop edition. It came in the mail yesterday. The disk is loaded into the computer when I used the command.

Thanks again!

---

### Post by stephenb on 2008-05-22
Then, that's why it isn't working. To upgrade from Feisty you first need the _alternate_ CD of _Gutsy_. If you don't have it already, you will have to download the ISO of that and burn it to disk. 

First you upgrade to Gutsy with that, then you can upgrade to Hardy. You won't be able to upgrade from Feisty with only the Hardy desktop CD. Also, if you want to upgrade from Gutsy to Hardy with CD only, you will need the _alternate_ Hardy CD as well.

On the other hand, you could do a clean install with that latest desktop edition you received. That would be a lot quicker and more trouble free. A lot of people are recommending clean installs over upgrades these days.

---

### Post by Muchohombre57 on 2008-05-22
Stephenb:

Once again thank you for your reply!

A clean install sounds great to me. I am not sure how to do it. Let me tell you what I have and do not have.

The computer I presently have 7.04 on is a slightly used "Everex Impact GC 3500" that originally had "Vista" on it. I completely erased "Vista" from the computer. I do not have the "Vista" restore disk.

As you know I do have the latest version of Ubuntu on disk. If you could tell me how to do a clean install I would greatly appreciate it!

Thank you!

---

### Post by stephenb on 2008-05-22
You can find plenty of info about clean installs on the Web. Here are a few links I found after a quick search:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://lifehacker.com/371194/first-look-at-ubuntu-804-hardy-heron-beta](http://lifehacker.com/371194/first-look-at-ubuntu-804-hardy-heron-beta)

I'd say it will be much the same as when you did your Feisty install. You just boot up from the CD and follow the instructions. (Your BIOS settings will need to configured to boot from the CD before the hard disk. It may do that already.)

Of course, a clean install means you'll have to back up everything you want to keep, including important config files, for example, in /etc. If you have partitions set up, I believe you can nominate which to overwrite and which to keep, but I'm not 100% sure on that. If you don't have partitions, it'll just wipe everything.  (For that, you just select "use entire disk" when the partitioner comes up.)

Remember, back up everything you want to keep onto some kind of external disk.

---

### Post by Muchohombre57 on 2008-05-23
Stephanb:

I went to one of the websites you posted and used the "Alternate CD" method of upgrading.

The install seemed to go fine except my monitor's display has diagonal lines running through it along with some ghosting. A problem I didn't have with 7.10.

I consider this a minor problem. I have listed another post under "General Help" and am hoping this glitch will be solved soon.

Thank you very much for your help!

---

