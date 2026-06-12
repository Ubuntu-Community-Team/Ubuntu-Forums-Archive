---
title: "&quot;A serious security issue&quot; for Xubuntu &quot;update&quot; as per research; Please see below."
date: 2016-04-29
forum: Installation &amp; Upgrades
---

### Post by David_Russell_Jaco on 2016-04-29
1)  I am having "a serious security problem" in updating re:  "There is no public key available for the following key IDs:  1397BC53640DB551," as per the computer upon completion of my requested update.  
2)  I thought I'd "repaired" this problem yesterday mid-afternoon, by [COLOR=#242729][FONT=Consolas]sudo aptitude install debian-keyring debian-archive-keyring.   [/FONT][/COLOR]
3)  However it's recurred again.
4)  I've been working on a "wine" link to a "picoscope6etaautomotive" program (a Microsoft program initially, by "wine" to Linux),  an "automotive oscilloscope" program. 
5)  This is for a "College class," re:  education.  I've had "no" success with the program's implementation through "wine."  
6)  Is the above identified, "no public key available for the key ID," linked to "wifi" as the "update" mechanism?
7)  Any wisdom re:  "key ID" problem (a serious security issue as per research)?
8)  Any wisdom re:  "Pico" oscilloscope "wine" program's (to Linux) difficulties?
9)  Are the two related "security" problems?
10)  Best solution?
11)  Thank you 
12)  Good Day.

---

### Post by QIII on 2016-04-29
Is there an expectation that the exercise be done with this software on a Windows machine?

---

### Post by oldos2er on 2016-04-29
>  I am having "a serious security problem" in updating re:  "There is no  public key available for the following key IDs:  1397BC53640DB551," as  per the computer upon completion of my requested update

```
gpg --keyserver pgp.mit.edu --recv-keys 1397BC53640DB551

gpg --export --armor 1397BC53640DB551 | sudo apt-key add -

sudo apt-get update
```

---

### Post by grahammechanical on 2016-04-29
Basically, the message means that the software package cannot be authenticated as coming from the owner of the software.

Explaining all this is beyond my skill set & my knowledge base and I do not think it is something that can be answered in a forum post. You need to read up on public key cryptography and how the Debian package manager works with it. Ubuntu is built on the Debian distribution. So, I guess the explanation given by the Debian web site is as good as any.

[https://en.wikipedia.org/wiki/Public-key_cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography)

[https://en.wikipedia.org/wiki/Pretty_Good_Privacy](https://en.wikipedia.org/wiki/Pretty_Good_Privacy)

[https://wiki.debian.org/SecureApt](https://wiki.debian.org/SecureApt)

> 6)  Is the above identified, "no public key available for the key ID," linked to "wifi" as the "update" mechanism?

No. The same error would appear if you had a wired connection to the router. WiFi connections as usually encrypted. But that kind of encryption is another story.

> 9)  Are the two related "security" problems?

I think the message regarding no public key available when running a system update/upgrade is a separate problem to the problem you are having getting a Windows automotive oscilloscope program running under wine.

Linking the two problems will only cause confusion. As regards the no public key available problem please run these two commands and post the output from each in this thread. Enclose the output in quote tags.

```
sudo apt-get update
sudo apt-get upgrade
```

In this way we will see for ourselves what the message is and it might give a clue as to the software package being referred to.

Regards.

---

### Post by gordintoronto on 2016-04-30
See this page: [https://www.picotech.com/downloads](https://www.picotech.com/downloads)

It says there is a picoscope for Linux. Since you need drivers for the computer to get data from the 'scope, there is almost zero chance you could ever get it running under Wine.

---

### Post by deadflowr on 2016-04-30
The key is a Google Repository error (probably for Chrome)
See:
[http://ubuntuforums.org/showthread.php?t=2322420]("http://ubuntuforums.org/showthread.php?t=2322420")

---

