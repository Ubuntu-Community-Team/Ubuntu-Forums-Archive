---
title: "Updates always fail. &quot;Failed to download repository information&quot; every time"
date: 2017-02-11
forum: Installation &amp; Upgrades
---

### Post by Alduins_Khajiit on 2017-02-11
Updates were not installed during installation of Ubuntu 16.04 LTS due to the option being grayed out. Now I cannot update whatsoever. It always fails in both 'Software and Updates' and in the terminal:

Software and Updates gives the following error message"

Failed to download repository information. Check your Internet connection. Details reads:
 W:The repository 'cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial Release' does not have a Release file., W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., W:See apt-secure(8) manpage for repository creation and user configuration details., E:Failed to fetch cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)/dists/xenial/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs, E:Some index files failed to download. They have been ignored, or old ones used instead.

the same details error occurs with *sudo apt-get update.* 

I am receiving system errors and errors all over the place with messages of obsolete software. but how am I supposed to get the latest software if it fails to download the software every time.

My internet is fine, I am typing from my Linux machine

---

### Post by Dennis N on 2017-02-11
Look at **Software and Updates > Other Software** tab. Be sure **cdrom** is unchecked. That may help.

---

### Post by Alduins_Khajiit on 2017-02-12
I removed the checkbox for 'cdrom'

Now I am getting a 

"Requires installation of untrusted packages

This requires installing packages from unauthenticated sources."

There is a 'settings' button but 'Unsupported Updates (Xernial-backports)' is already checked but I am still getting that error message. The only other option is 'OK' but that doesn't install anything and the update notifier doesn't go away.

---

### Post by Dennis N on 2017-02-12
So the problem in the title is solved (Failed to download repository information). As to the new problem,

"Requires installation of untrusted packages. This requires installing packages from unauthenticated sources."

This may help:
Can you identify the unauthenticated sources? If there were no further details in that message, try:
```
sudo apt-get update
```
which may give more details in the output, and see if any errors or warnings are shown, particularly about signing keys missing? If some repository (usually a PPA) is mentioned, open "software and updates" and uncheck that PPA in the "other software" tab. Run sudo apt-get update again, be sure there are no errors or warnings, then sudo apt-get upgrade.

---

### Post by Alduins_Khajiit on 2017-02-18
I had to wait until the next weekend to get back with you because of college classes all week long.

Here is the output of Sudo apt-get update. Same kind of error.

```
shrunken-human@Toilet:~$ sudo apt-get update
[sudo] password for shrunken-human: 
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease           
Hit:4 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:5 http://security.ubuntu.com/ubuntu xenial-security InRelease       
Get:6 https://download.01.org/gfx/ubuntu/16.04/main xenial InRelease [3,651 B]
Ign:6 https://download.01.org/gfx/ubuntu/16.04/main xenial InRelease
Fetched 3,651 B in 0s (4,007 B/s)
Reading package lists... Done
W: GPG error: https://download.01.org/gfx/ubuntu/16.04/main xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 56A3DEF863961D39
W: The repository 'https://download.01.org/gfx/ubuntu/16.04/main xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
shrunken-human@Toilet:~$ 


```

---

### Post by howefield on 2017-02-18
> **Alduins_Khajiit said:**
> ```
W: GPG error: https://download.01.org/gfx/ubuntu/16.04/main xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 56A3DEF863961D39
```

Try some of the solutions in this thread : [https://ubuntuforums.org/showthread.php?t=2344530](https://ubuntuforums.org/showthread.php?t=2344530)

There are many others.

---

### Post by Alduins_Khajiit on 2017-03-05
None of the suggestions listed in the thread worked for me. It is still telling me that there are untrusted sources for updates and refuses to update. I tried every fix in that thread, especially those of which people said worked. ...Except none of them worked for me.

Anything else I need to do?

---

### Post by oldos2er on 2017-03-06
You installed the missing key(s) and re-ran ```
sudo apt update
```?

---

### Post by Alduins_Khajiit on 2017-03-18
Yes I did and the same error occurs

I ran this

```
[COLOR=#2A2E2E][FONT=&amp]wget $(echo "https://download".01.org/gfx/RPM-GPG-GROUP-KEY-ilg) -O - | sudo apt-key add -[/FONT][/COLOR]
```


And I got this:

```
shrunken-human@Toilet:~$ wget $(echo "https://download".01.org/gfx/RPM-GPG-GROUP-KEY-ilg) -O - | sudo apt-key add -
--2017-03-18 09:23:01--  https://download.01.org/gfx/RPM-GPG-GROUP-KEY-ilg
Resolving download.01.org (download.01.org)... [sudo] password for shrunken-human: 23.74.75.94, 2600:1407:19:193::ae6, 2600:1407:19:191::ae6
Connecting to download.01.org (download.01.org)|23.74.75.94|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1760 (1.7K)
Saving to: ‘STDOUT’

-                   100%[===================>]   1.72K  --.-KB/s    in 0s      

2017-03-18 09:23:01 (325 MB/s) - written to stdout [1760/1760]





```


And the process stops right there doing nothing after that. Tells me there is a process running if I close the terminal. but says that no matter how long I wait. even several hours

---

### Post by oldos2er on 2017-03-18
Try this instead: ```
wget --no-check-certificate https://download.01.org/gfx/RPM-GPG-GROUP-KEY-ilg


sudo apt-key add RPM-GPG-GROUP-KEY-ilg
``` Let me know if it works or not.

---

### Post by Alduins_Khajiit on 2017-04-02
this is the output and it still isn't working. Still get the "Untrusted packages" error message

```
shrunken-human@Toilet:~$ wget --no-check-certificate https://download.01.org/gfx/RPM-GPG-GROUP-KEY-ilg
--2017-04-02 11:07:23--  https://download.01.org/gfx/RPM-GPG-GROUP-KEY-ilg
Resolving download.01.org (download.01.org)... 23.78.187.111, 2600:1407:f:19a::ae6, 2600:1407:f:18b::ae6
Connecting to download.01.org (download.01.org)|23.78.187.111|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1760 (1.7K)
Saving to: &#8216;RPM-GPG-GROUP-KEY-ilg&#8217;

RPM-GPG-GROUP-KEY-i 100%[===================>]   1.72K  --.-KB/s    in 0s      

2017-04-02 11:07:24 (429 MB/s) - &#8216;RPM-GPG-GROUP-KEY-ilg&#8217; saved [1760/1760]

shrunken-human@Toilet:~$ 
shrunken-human@Toilet:~$ 
shrunken-human@Toilet:~$ sudo apt-key add RPM-GPG-GROUP-KEY-ilg


```

```
This requires installing packages from unauthenticated sources.
```


```
shrunken-human@Toilet:~$ wget --no-check-certificate https://download.01.org/gfx/RPM-GPG-GROUP-KEY-ilg
--2017-04-02 11:07:23--  https://download.01.org/gfx/RPM-GPG-GROUP-KEY-ilg
Resolving download.01.org (download.01.org)... 23.78.187.111, 2600:1407:f:19a::ae6, 2600:1407:f:18b::ae6
Connecting to download.01.org (download.01.org)|23.78.187.111|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1760 (1.7K)
Saving to: &#8216;RPM-GPG-GROUP-KEY-ilg&#8217;

RPM-GPG-GROUP-KEY-i 100%[===================>]   1.72K  --.-KB/s    in 0s      

2017-04-02 11:07:24 (429 MB/s) - &#8216;RPM-GPG-GROUP-KEY-ilg&#8217; saved [1760/1760]

shrunken-human@Toilet:~$ 
shrunken-human@Toilet:~$ 
shrunken-human@Toilet:~$ sudo apt-key add RPM-GPG-GROUP-KEY-ilg
[sudo] password for shrunken-human: 
OK
shrunken-human@Toilet:~$ sudo apt-get update
Hit:1 http://archive.canonical.com/ubuntu xenial InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Hit:3 http://security.ubuntu.com/ubuntu xenial-security InRelease        
Hit:4 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease       
Hit:5 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease
Get:6 https://download.01.org/gfx/ubuntu/16.04/main xenial InRelease [3,651 B]
Ign:6 https://download.01.org/gfx/ubuntu/16.04/main xenial InRelease
Fetched 3,651 B in 0s (4,814 B/s)
Reading package lists... Done
W: GPG error: https://download.01.org/gfx/ubuntu/16.04/main xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 56A3DEF863961D39
W: The repository 'https://download.01.org/gfx/ubuntu/16.04/main xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.


```

---

### Post by oldos2er on 2017-04-03
Try ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 56A3DEF863961D39

sudo apt-get update
```

---

### Post by Alduins_Khajiit on 2017-04-09
Okay that worked. It's updating now.

---

### Post by oldos2er on 2017-04-09
Good! Would you please mark the thread 'Solved' under Thread Tools at the top of the page? It'll help others who might be having the same problem.

---

