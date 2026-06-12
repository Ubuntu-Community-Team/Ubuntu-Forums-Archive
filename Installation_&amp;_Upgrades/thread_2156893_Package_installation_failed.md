---
title: "Package installation failed"
date: 2013-06-23
forum: Installation &amp; Upgrades
---

### Post by iamnotbubba on 2013-06-23
I am really not sure why, Every time I get an update package for 13.04 I receive a installation failed message. I then go and check if I have the latest version. The message is then that I have the latest version. Am I doing something wrong? Is the computer updating correctly? 

iamnotbubba

---

### Post by Bashing-om on 2013-06-23
[COLOR=#000000]iamnotbubba; Hi ! Welcome to the forum.

In order to get a status on the package manager, do in terminal (key combo ctl+alt+t) :
```

sudo apt-get update
sudo apt-get upgrade

```
And if errors ...post the outputs back onto this thread - please use the code tag ("#") utility at the top of the post -
And we will advise you on actions to take !
[/COLOR][INDENT=3][COLOR=#000000]
just try'n to help

[/COLOR][/INDENT]

---

### Post by iamnotbubba on 2013-06-23
#utility 

Thank you very much for your help. The error I received,

```
2 not fully installed or removed.Need to get 0 B/12.4 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: error processing linux-image-3.8.0-19-generic (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of linux-image-extra-3.8.0-19-generic:
 linux-image-extra-3.8.0-19-generic depends on linux-image-3.8.0-19-generic; however:
  Package linux-image-3.8.0-19-generic is not configured yet.
No apport report written because MaxReports is reached already


dpkg: error processing linux-image-extra-3.8.0-19-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.8.0-19-generic
 linux-image-extra-3.8.0-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```


iamnotbubba

---

### Post by Bashing-om on 2013-06-23
[COLOR=#000000]iamnotbubba; 
Let's see what you are running now before undertaking to get the linux-image updated:
```

lsb_release -a
uname -r

```
[/COLOR][INDENT=2][COLOR=#000000]
one step at a time = progress

[/COLOR][/INDENT]

---

### Post by iamnotbubba on 2013-06-23
```
No LSB modules are available.Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring
jazlmden@ubuntu:~$ uname -r
3.8.0-23-generic



```

iamnotbubba

---

### Post by Bashing-om on 2013-06-23
iamnotbubba; Hey.

Looking good:
Try this:
```

sudo dpkg --remove linux-generic-pae
sudo apt-get install linux-generic-pae
sudo apt-get update
sudo apt-get upgrade

```[INDENT=2]
should workie great, last long time

[/INDENT]

---

### Post by iamnotbubba on 2013-06-23
Thank you so much for your time. However i am not sure it worked. Did I do something wrong?

```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.2 not fully installed or removed.
Need to get 0 B/12.4 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: error processing linux-image-3.8.0-19-generic (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of linux-image-extra-3.8.0-19-generic:
 linux-image-extra-3.8.0-19-generic depends on linux-image-3.8.0-19-generic; however:No apport report written because MaxReports is reached already
                                                                   No apport report written because MaxReports is reached already


  Package linux-image-3.8.0-19-generic is not configured yet.


dpkg: error processing linux-image-extra-3.8.0-19-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.8.0-19-generic
 linux-image-extra-3.8.0-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

iamnotbubba

---

### Post by Bashing-om on 2013-06-23
iamnotbubba;
Do not know why an old image file is giving us such heartburn.. Let's get direct with it:
terminal codes:
```

sudo apt-get --purge remove linux-image-3.8.0-19-generic
sudo apt-get --purge remove linux-headers-3.8.0-19-generic
sudo apt-get --purge remove linux-image-extra-3.8.0-19-generic
sudo update-grub  ##just to be on the safe side

```

Any errors now ?[INDENT=2]
where there is a will there is a way

[/INDENT]

---

### Post by iamnotbubba on 2013-06-23
ok done

iamnotbubba

---

### Post by Bashing-om on 2013-06-23
[COLOR=#000000]iamnotbubba; Hey.
Regret the delay in getting back to you .. Deeply involved in another thread rather deep.

Looking good ?
what results now:
```
sudo apt-get update
sudo apt-get upgrade

```
[/COLOR][INDENT][COLOR=#000000]
light shines at the end of the tunnel [/COLOR][/INDENT]

---

### Post by iamnotbubba on 2013-06-23
No worries, went to get ice cream.

Still didn't work. Tried the purge codes again

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  language-pack-en language-pack-en-base linux-headers-3.8.0-19
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-3.8.0-19-generic*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 33.6 MB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: error processing linux-image-3.8.0-19-generic (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.8.0-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

I got this error message, does this mean anything?

iamnotbubba

---

### Post by Bashing-om on 2013-06-23
iamnotbubba; Strange and stranger....

Ok, let us follow what dpkg suggest. and try and install it prior to (un-)installing it:
```
sudo apt-get install --reinstall linux-image-3.8.0-19-generic
```

[INDENT][INDENT]will it (re-)install ?[/INDENT][/INDENT]

---

### Post by iamnotbubba on 2013-06-23
Yay, Shall I input this code next?

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get upgrade[/FONT][/COLOR]
```

iamnotbubba

---

### Post by Bashing-om on 2013-06-23
[COLOR=#000000]iamnotbubba; Sure !

Then a tale will be told ...all is well in the package manager's world .
[/COLOR][INDENT=3][COLOR=#000000]
where there is a will there is a way

[/COLOR][/INDENT]

---

### Post by iamnotbubba on 2013-06-23
YOU ARE AWESOME!!!!!! 

```
jazlmden@ubuntu:~$ sudo apt-get upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



```

That looks better!

iamnotbubba

---

### Post by Bashing-om on 2013-06-23
iamnotbubba; Nawhhh ->

ubuntu's package manager is awesome...
It told us to start with it needed some help, we gave it some things to chew on ,,, and finally it came back and told us what we needed to do.

That smart boy also suggested:
> 
The following packages were automatically installed and are no longer required:
  language-pack-en language-pack-en-base linux-headers-3.8.0-19
Use 'apt-get autoremove' to remove them.

```

sudo apt-get autoremove language-pack-en language-pack-en-base linux-headers-3.8.0-19

```
And that will remove the image that you just (re-)installed ! as per suggestion.

[INDENT][INDENT]just 1 more reason; ubuntu, operating system of choice[/INDENT][/INDENT]

---

### Post by iamnotbubba on 2013-06-23
You spent time to help me today, I really appreciate you. This is another reason I have abandoned the others. There is no support like this for the more commercial systems like mac or windows. I am truly grateful. 

iamnotbubba

---

### Post by Bashing-om on 2013-06-23
[COLOR=#000000]iamnotbubba;

Not a problem ..........this is open source !
We are all in this together.

If the situation now is all under control, please mark this thread as solved; aides others seeking a solution and helps keep the forum tidy:
[/COLOR]Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.
[INDENT=3]
all's well that ends well

[/INDENT]

---

