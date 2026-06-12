---
title: "Power managment service on KDE keeps failing to start on startup."
date: 2017-08-14
forum: Installation &amp; Upgrades
---

### Post by termibuntu on 2017-08-14
Hello. I am using Kubuntu 17.04 and I it get this error when I go in System Settings -> Power Management: 
`Power Management configuration module could not be loaded. The Power Management service appears not to be running. This can be solved by starting or scheduling it inside Startup & Shutdown.` 
But i see no option in Startup and Shutdown. Not only do I get this error, I don't have the power indicator which is meant to be there in the task bar. This is very annoying as I'm using a laptop with a battery that I don't know the percentage of. I saw it disappear while I was updating the kernel, but booting my previous kernel didn't show it up, either. This may also be about the package "powerdevil". It would be great if anyone could help me, since I don't want to reinstall Kubuntu. I have made myself at home ever since I installed Kubuntu, so I appreciate any help. Attached is the error, and if you also look in the task bar, there is no power indicator. Thanks in advance.

---

### Post by vasa1 on 2017-08-14
So what does```
ps axjf | grep -i power
```show?

I get```
$ ps axjf | grep -i power
    1  1081  1081  1081 ?           -1 Ssl      0   0:00 /usr/lib/upower/upowerd
 1392  1472  1367  1367 ?           -1 Sl    1001   0:00  |   \_ /usr/lib/x86_64-linux-gnu/libexec/org_kde_powerdevil
 7435  7450  7449  7435 pts/1     7449 S+    1001   0:00      \_ grep --color=auto -i power
$ 
```

Also, please try```
apt policy upower
```

And do you have the *kded5* package?

BTW, I googled for *kubuntu "The Power Management service appears not to be running"*. Quite a few hits, some of them for other KDE distros. I can't help much more because I have Kubuntu 16.04.

---

### Post by termibuntu on 2017-08-16
Hi. Sorry for not being here.... the indicator was back but won't come back anymore. :(
Here are the outputs: 
ps axjf | grep -i power shows:
```

    1  1021  1021  1021 ?           -1 Ssl      0   0:00 /usr/lib/upower/upowerd
 2034  2051  2050  2034 pts/1     2050 S+    1000   0:00  |   |           \_ grep --color=auto -i power
 1183  1245  1149  1149 ?           -1 Sl    1000   0:00  |   \_ /usr/lib/i386-linux-gnu/libexec/org_kde_powerdevil
```

apt policy upower shows this:

```
upower:
  Installed: 0.99.4-4
  Candidate: 0.99.4-4
  Version table:
 *** 0.99.4-4 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) zesty/main i386 Packages
        100 /var/lib/dpkg/status
```


and yes, I do have the package "kded5". Its running now. I tried Googleing and there wasn't anything for Kubuntu.
BTW how do you do code tags?

---

### Post by termibuntu on 2017-08-16
Somehow, it reappeared. Ill do a few reboots to make sure. Attached is a screen shot of how it's back.

---

### Post by vasa1 on 2017-08-16
> **termibuntu said:**
> ...
BTW how do you do code tags?
When you start a new thread or post in an existing thread using "Reply With Quote" or "Adv Reply", you'll see an icon that looks like **#** above the posting area's text box. Single-click on it. Automatically, you'll see [noparse]```

```[/noparse] appear in the text area where the insertion cursor is located. Simply paste your content from the terminal between the opening [noparse]```
[/noparse] and closing [noparse]
```[/noparse] tags.

In case you use the "Reply to Thread" or "Quick Reply" options, the **#** icon will not appear: these options provide a minimal set of icons. In that case you can carefully type in the tags yourself or click on "Go Advanced" below the posting area's text box to make the **#** icon (and other icons) appear.

---

### Post by vasa1 on 2017-08-16
One other point, if you're on zesty, you may want to install kubuntu-backports which is being actively maintained. See [https://www.kubuntuforums.net/showthread.php?t=72006](https://www.kubuntuforums.net/showthread.php?t=72006)

There'll be quite a few updates so don't bother if you have bandwidth limitations!

---

### Post by termibuntu on 2017-08-16
Thanks for showing me how to do the code tags!
```
test
```

Also, I already am on the version on KDE Plasma from the backports repository. But, thanks for suggesting that! 
BTW, I have great bandwidth so thats not a problem.

---

