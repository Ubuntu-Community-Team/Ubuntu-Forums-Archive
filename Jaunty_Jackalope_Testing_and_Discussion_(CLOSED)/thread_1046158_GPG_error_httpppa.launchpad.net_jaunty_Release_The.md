---
title: ": GPG error: http://ppa.launchpad.net jaunty Release: The following signatures"
date: 2009-01-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-01-21
The last 3 times I have updated, this missing key keeps coming up. Can some one direct me to the public key?
[B]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CA1F91146F087E5A
[/B]

---

### Post by taavikko on 2009-01-21
This is for the first key,

```
gpg --keyserver keyserver.ubuntu.com --recv 0c713da6
```
```
gpg --export --armor 0c713da6 | sudo apt-key add -
```

Do the same for the other key...
Last 8 digits...

Probably good idea to tell the problem to owner of ppa?

---

### Post by DougieFresh4U on 2009-01-21
> **taavikko said:**
> This is for the first key,

```
gpg --keyserver keyserver.ubuntu.com --recv 0c713da6
```
```
gpg --export --armor 0c713da6 | sudo apt-key add -
```

Do the same for the other key...
Last 8 digits...

Probably good idea to tell the problem to owner of ppa?

Thanks, did get one taken care of but I am not sure about the second as terminal says this:
[B]dougie@DougiesLeanMachine:~$ gpg --export --armor 0c713da6 | sudo apt-key add - 0c713da6
OK
[/B]
maybe I did it wrong as when I run terminal I am still getting this:
[B]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CA1F91146F087E5A
[/B]

---

### Post by taavikko on 2009-01-21
Like I said, do the same thing for the second key,
that's why the error/warning about the other key...


Well, cause i started, might as well finish it :D
```
gpg --keyserver keyserver.ubuntu.com --recv 6F087E5A
```
```
gpg --export --armor 6F087E5A | sudo apt-key add - && sudo apt-get update
```

Is the error solved?

---

### Post by taavikko on 2009-01-21
> Thanks, did get one taken care of but I am not sure about the second as terminal says this:
dougie@DougiesLeanMachine:~$ gpg --export --armor 0c713da6 | sudo apt-key add - 0c713da6
OK

The command I wrote to you was complete, you didn't have to add <key> after the: apt-key add - .
but writing it doesn't seem to matter.

What i meant that you do the same two codes, for the second key.
those last 8 digits are the ones that matters...

---

### Post by DougieFresh4U on 2009-01-21
All fixed. Sorry for my ignorance.](*,)
Thank you very much.
Dougie

---

### Post by taavikko on 2009-01-21
> **DougieFresh4U said:**
> All fixed. Sorry for my ignorance.](*,)
Thank you very much.
Dougie

Your welcome, but that's not an ignorance, since that's a bliss.
If you haven't had to deal with these kind of problems, how were you supposed to know?

btw, remember to mark thread solved ;)

---

### Post by DougieFresh4U on 2009-01-21
> **taavikko said:**
> btw, remember to mark thread solved ;)
 The 'solved' marker is gone as well as the 'thanks' button.
They are working it, I had read a thread concerning that issue

---

### Post by taavikko on 2009-01-21
> **DougieFresh4U said:**
> The 'solved' marker is gone as well as the 'thanks' button.
They are working it, I had read a thread concerning that issue

I noticed the thanks button yesterday, but that thread tools also missing functions... my my, hard day at rt@ubuntu,com

but, happy to be at your service.

---

### Post by ronacc on 2009-01-21
yeah the forums ahve had alot of downtime lately .

---

### Post by tawmas on 2009-01-21
> **taavikko said:**
> This is for the first key,

```
gpg --keyserver keyserver.ubuntu.com --recv 0c713da6
```
```
gpg --export --armor 0c713da6 | sudo apt-key add -
```

Do the same for the other key...
Last 8 digits...

Probably good idea to tell the problem to owner of ppa?

Thanks, I was searching for the same information!

Anyway, keyserver.ubuntu.com is failing for me (times out), while Internet connectivity seems to be otherwise good and people here seem not to have this issue... mmm... Corporate firewall, perhaps? What protocols/ports are used for this?

---

### Post by taavikko on 2009-01-21
> **tawmas said:**
> Thanks, I was searching for the same information!

Anyway, keyserver.ubuntu.com is failing for me (times out), while Internet connectivity seems to be otherwise good and people here seem not to have this issue... mmm... Corporate firewall, perhaps? What protocols/ports are used for this?

You could use few of keyservers found on net.
I cannot be sure what servers hosts keys, since now way of knowing where the owner has published his key...

---

### Post by tawmas on 2009-01-21
> **taavikko said:**
> You could use few of keyservers found on net.
I cannot be sure what servers hosts keys, since now way of knowing where the owner has published his key...

Thanks, it was the firewall, but I was able to retrieve the key through another machine.

BTW, isn't the key "owner" Launchpad itself? As far as I understand, PPA keys are autogenerated...

---

### Post by caryb on 2009-01-21
Another one for packagekit

```
gpg --keyserver keyserver.ubuntu.com --recv 9BFC84D3205358CF


gpg --export --armor 9BFC84D3205358CF | sudo apt-key add -
```

---

### Post by unixel on 2009-01-22
I cannot get t the keyserver, our company firewall blocks it and I cannot get it from another machine outside the network due to ssh being blocked as well. 

Any other method to do this ? 

Regards

---

### Post by tawmas on 2009-01-22
> **unixel said:**
> I cannot get t the keyserver, our company firewall blocks it and I cannot get it from another machine outside the network due to ssh being blocked as well. 

Any other method to do this ? 

Regards

I guess you can ask a friend to get the key and send it to you via e-mail. Your friend needs to do:

```
gpg --keyserver keyserver.ubuntu.com --recv 9BFC84D3205358CF
gpg --export --armor 9BFC84D3205358CF > key.asc
```

And attach the file key.asc

Then you can import the key with

```
cat key.asc | sudo apt-key add -
```

---

### Post by DougieFresh4U on 2009-01-22
double post, sorry

---

### Post by DougieFresh4U on 2009-01-22
Saw this in another thread:

[B]```
Important: Over the next few weeks, Launchpad is generating keys for each PPA. While this is happening, one of two things will happen when you install software from a PPA:

* Ubuntu will warn you that the package is unsigned.
* Ubuntu will tell you that it can't verify the key used to sign the package. Visit the PPA's overview page to confirm the key's fingerprint and then continue if you are happy that the package is correctly signed.
https://help.launchpad.net/Packaging...20repositories
```[/B]

---

### Post by fpalmer_35 on 2009-01-24
> **tawmas said:**
> I guess you can ask a friend to get the key and send it to you via e-mail. Your friend needs to do:

```
gpg --keyserver keyserver.ubuntu.com --recv 9BFC84D3205358CF
gpg --export --armor 9BFC84D3205358CF > key.asc
```

And attach the file key.asc

Then you can import the key with

```
cat key.asc | sudo apt-key add -
```


I guess [this]("http://iadetout.free.fr/joomla/index.php?option=com_content&view=article&id=36:probleme-de-signature-de-paquets&catid=4:ubuntu&Itemid=14") could help you. The syntaxe is lightly different.

---

### Post by ubulette on 2009-01-24
> **taavikko said:**
> Probably good idea to tell the problem to owner of ppa?

If you look closely at my [PPA]("https://launchpad.net/~fta/+archive"), it was mentioned in the whiteboard since it is signed. There's no other communication channel i'm afraid.

---

### Post by taavikko on 2009-01-24
> **ubulette said:**
> If you look closely at my [PPA]("https://launchpad.net/~fta/+archive"), it was mentioned in the whiteboard since it is signed. There's no other communication channel i'm afraid.

Thanks for the added info, My reply was just to help him to add the key,
Haven't looked at your ppa ;) 
and for the informing the owner, hence the question mark?

---

### Post by blackgr on 2009-01-24
[http://ubuntuforums.org/showthread.php?t=1047743](http://ubuntuforums.org/showthread.php?t=1047743)

---

### Post by andrewsomething on 2009-01-25
Another thing ppa owners can do is create a keyring package for their ppa that automatically adds their key to apt.

For instance, users of my PPA (I'd guess there's only a handful) can just run:

sudo apt-get install andrewsomething-ppa-keyring



[https://edge.launchpad.net/~andrewsomething/+archive/ppa](https://edge.launchpad.net/~andrewsomething/+archive/ppa)

---

### Post by modone on 2009-01-27
Perfect - Thanks taavikko :D

---

### Post by king_arthur on 2009-02-01
This did the trick also for me, and it made dist-upgrade possible at last.

Many many thanks. :-)

I wonder, however, why the issue started in first instance..

---

### Post by dbram32 on 2009-02-13
Hey, Thanks Papa Smurf! Worked great for me!! After weeks of trying to chase down the cure.

 taavikko
Way Too Much Ubuntu
 
taavikko's Avatar 

You Da Man!

---

### Post by forger on 2009-02-14
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by coldraught on 2009-02-20
taavikko,
Thanks for the solution to this.  It fixed my issue as well.

---

### Post by sadicote on 2009-04-03
Hi, i tried following taavikko's instructions, but i seemed to have done something wrong and can't see it.

sade@sade-desktop:~$ gpg --keyserver keyserver.ubuntu.com –recv 5ADC2037
usage: gpg [options] [filename]
sade@sade-desktop:~$ gpg --export --armor 5ADC2037 | sudo apt-key add - && sudo apt-get update
[sudo] password for sade: gpg: WARNING: nothing exported

gpg: no valid OpenPGP data found.

My error message is "... NO_PUBKEY 8AB767895ADC2037" I have already upgraded to Jaunty, this is the error message i get after adding the apt lines for clamav and reloading Synaptic.

---

### Post by ubulette on 2009-04-03
> **sadicote said:**
> 
sade@sade-desktop:~$ gpg --keyserver keyserver.ubuntu.com [COLOR="Red"]–recv[/COLOR] 5ADC2037
usage: gpg [options] [filename]


should be --recv

---

### Post by sadicote on 2009-04-03
I really need to get my eyes rechecked and get new spectacles. I apologize for all the trouble i have caused these past few days because of that.Thank you all for your infinite patience.

---

