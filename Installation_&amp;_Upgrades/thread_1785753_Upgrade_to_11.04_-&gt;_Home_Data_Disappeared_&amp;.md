---
title: "Upgrade to 11.04 -&gt; Home Data Disappeared &amp; Encrypted Files"
date: 2011-06-18
forum: Installation &amp; Upgrades
---

### Post by AchBlewy on 2011-06-18
[SIZE=2]I  recently upgraded to 11.04 using the Upgrade Manager over the network.  The upgrade seemed to go fine, I think there was some minor hardware  complaints but everything seemed fine except that all the data in my  home directory was apparently gone. I have no idea if this is important, but during  the upgrade dialog I was asked if I wanted to get the encryption  pass-phrase and clicked no, but opened a terminal window and got it  anyway. After the upgrade I noticed that there exists a .Private folder with encrypted  sub-folders/files. Is it possible that my data is hiding here? I fiddled  around a bit following some directions about how to manually decrypt  those directories but without apparent success. My question remains, is it  possible my data is hiding encrypted in the .Private directory? If so  what is the correct procedure to get it back into my home directory?[/SIZE] [SIZE=2]
  
[/SIZE] [SIZE=2]Then I shut down and restarted the system using a 10.10 CD.  Mounted the interesting partition and peaked into my home directory. The  data is all there, unencrypted. That is nice. I went ahead and tarred  up the interesting parts and backed it up to a memory stick. 
  
 There are still many possibilities about what is going on here, and I  still don't know what to do to get my system running under 11.04 with my data where it should be. I will  enumerate a few possible explanations: 
[/SIZE][INDENT][SIZE=2] Possibility (1): My home  directory is normally encrypted (the data is encrypted on a cold disk),  but 11.04 does not know (and I don't know) how to unencrypt it, however,  10.10 unencrypts the thing without me having to do anything (somehow this  does not seem likely). [/SIZE]

[SIZE=2] Possibility (2): The data is unencrypted on the  cold disk, but 11.04 goes ahead and encrypts the thing (a) on boot up or  (b) on log in and places it in the .Private directory. [/SIZE]

[SIZE=2] Possibility (3):  11.04 does not know where my real home directory is and recreates an  empty new one with a standard .Private directory filled with who knows  what.[/SIZE]
[/INDENT][SIZE=2]     I think I can easily check Possibility 2b. Help explanations please!
[/SIZE]

---

### Post by Shadow00Shadow on 2011-06-20
Bottom line is that you have recovered your lost files

Why not just install a clean copy of 11.04, then add the files to a     new directory, reinstall each program, then copy the sub-directories     from the old version over writing the new version's sub-directories     (ie.  address books, emails etc.).  

The important thing is that you have perhaps identified a problem with 11.04, I have noticed at least one other response that addresses the same problem.


S00S

---

### Post by AchBlewy on 2011-06-20
Thanks for the idea. I did think about that (adding in my now backed up mission critical files after a fresh install). I am somewhat reluctant to do this. The point is to try to understand what happened. It is very  distressing to have your files disappear like that for no apparent  reason. 

Is it really true that nobody on this forum has a  clue about what is going on here? This has to be a very basic issue. Or if I have done something idiotically stupid, then what did I do?

Also, thanks for pointing out that at least one other person has had a similar issue, but there is no explanation given: [http://ubuntuforums.org/showthread.php?t=1743351](http://ubuntuforums.org/showthread.php?t=1743351)

---

### Post by Bruno Lalande on 2011-09-16
I think I've found some sort of explanation.

Bottom line: move /home/.ecryptfs/<your_username> to anywhere else, reboot, and your lost home is there again.

I had exactly the same issue, and was puzzled as well that df was still seeing my data in terms of space used while I couldn't find it anywhere. You actually helped me a lot by describing what you did with your live CD : since simply mounting the relevant partition within the live CD suffices to recover your home at its usual place while doing the same within 11.04 doesn't give the same result, the reason could only be that something was "hiding" your normal home.

So I went ahead and re-mounted my partition to some temp directory within 11.04 directly. It worked: temp/home/<myuser> contained my lost home.

FYI the .ecryptfs directory you have in /home is indeed an encrypted directory, but the one of your NEW home. Not the one you're interested in. And the .Private in your home is just a link to it. What happens is that when you start, it first mounts the partition (so at that step you probably have your old home at the right place) and then it decrypts+mounts the encrypted new home and places it at... /home/<username>. So this path no longer points you to your old home, which is hidden by the fresh one.

So, just move /home/.ecryptfs/<username> to anywhere else to prevent it from being mounted and thus hiding your real home.

There's probably something cleaner to do, involving a better understanding of all that. I think I'll stick to that for now. But it is obvious to me that there's a bug in the upgrade process - or at least something misleading that makes us make the wrong choice at some point.

Bruno

---

### Post by elundmark on 2012-05-31
My folders were also lost, but it happened long after I did a fresh installation of 12.04 (w/ home ecryption).

I found that [FONT="Courier New"]**ls ~**[/FONT] shows "double" folders (and some files) of ex: 

Music Music Templates Templates Downloads Downloads my_custom_dir Videos Videos .config .config [...]

So I did ```
mv Music Music_old
```, and voilá, my original Music folder is now "Music", and "Music_old" is an empty folder. So weird...

And because this happened to many other (system) files like .config and .gconf / .dconf, ALL my settings were reset to default.

I have a lot of [FONT="Courier New"]**mv**[/FONT] commands ahead of me, gonna take all freckin' night I reckon... sometimes Ubuntu makes me sooo angry...

---

