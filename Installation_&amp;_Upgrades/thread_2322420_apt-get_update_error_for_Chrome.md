---
title: "apt-get update error for Chrome"
date: 2016-04-27
forum: Installation &amp; Upgrades
---

### Post by fazil2 on 2016-04-27
I'm getting the following GPG error when I run apt-get update on Ubuntu 16.04

*Reading package lists... Done*
*W: [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:) Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)*
*W: There is no public key available for the following key IDs:*
*1397BC53640DB551*

Seems to be an identified issue on Debian but I have come across only one report on Ubuntu.

---

### Post by drm200 on 2016-04-27
I am using 14.04
I updated chrome yesterday via the software center.  I also receive this error after running sudo apt-get update:

[I]There is no public key available for the following key IDs:
*1397BC53640DB551*[/I]

---

### Post by pedrinho98765 on 2016-04-28
Also getting this error.

```
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: There is no public key available for the following key IDs:
1397BC53640DB551
```

---

### Post by QIII on 2016-04-28
Hello!

[This]("https://wiki.debian.org/Teams/Apt/Sha1Removal") may be of interest to you.  The upshot appears to be that *_Google_* needs to fix this.

---

### Post by allandeamon on 2016-04-28
> **QIII said:**
> Hello!

[This]("https://wiki.debian.org/Teams/Apt/Sha1Removal") may be of interest to you.  The upshot appears to be that *_Google_* needs to fix this.

Well, the week digest algorithm warning seems to be there for a while, but the the error of missing key appeared to me 2 hours ago. I use Debian Sid (Unstable), with google chrome, which the repository seems to be the one causing both trouble. 

> 
W: There is no public key available for the following key IDs:
1397BC53640DB551

---

### Post by drm200 on 2016-04-28
I'm using 14.04 .... It is interesting that I do not receive the "weak digest algorithm" error

I only receive this warning: [COLOR=#000000]*W: There is no public key available for the following key IDs:*[/COLOR]
[COLOR=#000000][I]1397BC53640DB551

[/I][/COLOR]I do not know how to determine what this key ID references ... I only know that I noticed it today while doing a "sudo apt-get update" after having upgraded chrome and some Ubuntu security updates.  So I am unable to say it is associated with chrome.

---

### Post by dwarfjazzer on 2016-04-28
[h=1]wget -q -O - [https://dl.google.com/linux/linux_signing_key.pub](https://dl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -[/h]That will fix it

Source:
[https://www.reddit.com/r/linux4noobs/comments/4grdo7/an_error_occurred_w_there_is_no_public_key/](https://www.reddit.com/r/linux4noobs/comments/4grdo7/an_error_occurred_w_there_is_no_public_key/)

---

### Post by skyre2 on 2016-04-28
That command fixed for me```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 1397BC53640DB551
```[source]("https://www.reddit.com/r/linux4noobs/comments/4grdo7/an_error_occurred_w_there_is_no_public_key/d2k4ucy")

---

### Post by dmferrari on 2016-04-28
> **dwarfjazzer said:**
> **wget -q -O - [https://dl.google.com/linux/linux_signing_key.pub](https://dl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -**

That will fix it

Source:
[https://www.reddit.com/r/linux4noobs/comments/4grdo7/an_error_occurred_w_there_is_no_public_key/](https://www.reddit.com/r/linux4noobs/comments/4grdo7/an_error_occurred_w_there_is_no_public_key/)

This worked for me. Thanks!

---

### Post by fazil2 on 2016-04-28
None of the above commands worked for me. I guess have to wait till Google fixes it in the next release for Chrome

---

### Post by QDR06VV9 on 2016-04-28
> **QIII said:**
> Hello!

[This]("https://wiki.debian.org/Teams/Apt/Sha1Removal") may be of interest to you.  The upshot appears to be that *_Google_* needs to fix this.
Hi there:D
This is what I get from your link.
Kind Regards

---

### Post by vasa1 on 2016-04-28
[https://wiki.debian.org/Teams/Apt/Sha1Removal](https://wiki.debian.org/Teams/Apt/Sha1Removal) seems okay now.

---

### Post by QDR06VV9 on 2016-04-28
He he he I guess no soup for me today..
> [SIZE=2]Forbidden[/SIZE]
<p>You are not allowed to access this!</p>



---

### Post by Poleh on 2016-04-28
> **dwarfjazzer said:**
> [h=1]wget -q -O - [https://dl.google.com/linux/linux_signing_key.pub](https://dl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -[/h]That will fix it

Source:
[https://www.reddit.com/r/linux4noobs/comments/4grdo7/an_error_occurred_w_there_is_no_public_key/](https://www.reddit.com/r/linux4noobs/comments/4grdo7/an_error_occurred_w_there_is_no_public_key/)

I can confirm this worked for me too: Linux mintyfresh 3.19.0-32-generic #37~14.04.1-Ubuntu SMP Thu Oct 22 09:41:40 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by tusharsonawane on 2016-04-30
Perfect. this worked for me

 sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 1397BC53640DB551

---

### Post by ziawiki on 2016-04-30
> **dwarfjazzer said:**
> **wget -q -O - [https://dl.google.com/linux/linux_signing_key.pub](https://dl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -**

That will fix it

Source:
[https://www.reddit.com/r/linux4noobs/comments/4grdo7/an_error_occurred_w_there_is_no_public_key/](https://www.reddit.com/r/linux4noobs/comments/4grdo7/an_error_occurred_w_there_is_no_public_key/)

Thank you, this fixed it.

---

### Post by rudder2 on 2016-05-01
> **dwarfjazzer said:**
> **wget -q -O - [https://dl.google.com/linux/linux_signing_key.pub](https://dl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -**

That will fix it

Source:
[https://www.reddit.com/r/linux4noobs/comments/4grdo7/an_error_occurred_w_there_is_no_public_key/](https://www.reddit.com/r/linux4noobs/comments/4grdo7/an_error_occurred_w_there_is_no_public_key/)

Thank you!!  This fixed it for me as well.

---

### Post by carlos-garza on 2016-05-02
probably forgot to run as sudo.
Try "[B]sudo wget -q -O - [https://dl.google.com/linux/linux_signing_key.pub](https://dl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -" if your getting a permission denied type error message. 
Otherwise show us the error message your getting so we can figure it out.
[/B]

---

### Post by Pythog on 2016-05-03
> **fazil2 said:**
> None of the above commands worked for me. I guess have to wait till Google fixes it in the next release for Chrome
Seems to be the case here. with me too.
I used all keys mentioned in my error report, using this command:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991

```
See image:
[ATTACH=CONFIG]268805[/ATTACH]
Example output:
[HTML]my-usrname@my-machine-name:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991Executing: /tmp/tmp.cCJqsw4POV/gpg.1.sh --recv-keys--keyserverkeyserver.ubuntu.com4CCA1EAF950CEE4AB83976DCA040830F7FAC5991gpg: requesting key 7FAC5991 from hkp server keyserver.ubuntu.comgpg: key 7FAC5991: "Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>" 30 new signaturesgpg: Total number processed: 1gpg:         new signatures: 30[/HTML]

---

### Post by HiRez_L on 2016-05-03
[B]wget -q -O - [https://dl.google.com/linux/linux_signing_key.pub](https://dl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -

worked for me, thanks![/B]

---

### Post by tom581 on 2016-05-04
Thank you. That fixed it for me.

---

### Post by rylyeh on 2016-05-04
> **skyre2 said:**
> That command fixed for me```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 1397BC53640DB551
```[source]("https://www.reddit.com/r/linux4noobs/comments/4grdo7/an_error_occurred_w_there_is_no_public_key/d2k4ucy")

Worked great for me on Mint 17!

---

### Post by Merrattic on 2016-05-08
> **wget -q -O - [https://dl.google.com/linux/linux_signing_key.pub](https://dl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -**

Also sorted for me. Thank you :)

but the problem came back 24 hours later :(

then soon after it went away again :)

manana ;)

---

### Post by michaelmcole on 2016-05-16
Still hasn't fixed it for me;

```
W:http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1), 

W:http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 3B068FB4789ABE4AEFA3BB491397BC53640DB551 uses weak digest algorithm (SHA1), 

W:http://dl.google.com/linux/musicmanager/deb/dists/stable/Release.gpg: Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1), 

E:Failed to fetch http://dl.google.com/linux/musicmanager/deb/dists/stable/Release  
No Hash entry in Release file /var/lib/apt/lists/dl.google.com_linux_musicmanager_deb_dists_stable_Release which is considered strong enough for security purposes, 

E:Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by hazemnoor on 2016-05-18
This one worked for me, Thanks 
> **skyre2 said:**
> That command fixed for me```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 1397BC53640DB551
```[source]("https://www.reddit.com/r/linux4noobs/comments/4grdo7/an_error_occurred_w_there_is_no_public_key/d2k4ucy")

---

### Post by John_Louie_Silvest on 2016-05-18
I don't know if it would work for all of you, or if you are willing to upgrade.. apt-get upgrade did it for me, btw before this was I already running 16.04.. so... yeah.. it was basically it. good luck.

---

### Post by Chelidze on 2016-06-01
Still getting this issue

```
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 3B068FB4789ABE4AEFA3BB491397BC53640DB551 uses weak digest algorithm (SHA1)


```

---

### Post by gregory-cook on 2016-06-15
This command worked for me after updating from 12.04 --> 14.04 and adding [arch=amd64] per this post: [http://www.omgubuntu.co.uk/2016/03/fix-failed-to-fetch-google-chrome-apt-error-ubuntu](http://www.omgubuntu.co.uk/2016/03/fix-failed-to-fetch-google-chrome-apt-error-ubuntu)

Thanks!

---

### Post by JuddRogers on 2016-08-14
+1 for #8

---

### Post by stewate4 on 2016-09-01
This worked for me
First get the key from the keyserver using gpg
 **gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 1397BC53640DB551**
then feed it to apt-key with
**gpg -a --export 1397BC53640DB551 | sudo apt-key add -**

---

### Post by howefield on 2016-09-01
Think we can close this bump thread now.

---

