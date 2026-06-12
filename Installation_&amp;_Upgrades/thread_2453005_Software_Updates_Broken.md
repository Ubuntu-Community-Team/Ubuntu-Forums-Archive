---
title: "Software Updates Broken"
date: 2020-11-01
forum: Installation &amp; Upgrades
---

### Post by kenbright on 2020-11-01
I just upgraded to  20.04 on Dell Vostro 1510 laptop Tried to install wine and an application but things have gone  wrong!Software won't update from Software updater and I can't remove the  Wine packages from Other software it just hangs and gives the same  message I get when - see the next bit Tried an update and got the following message in Terminal
 E:Malformed entry 52 in list file /etc/apt/sources.list (Component)
E: The list of sources could not be read.
 I gather I need to purge the sources list? but don't know how to go about it

---

### Post by coffeecat on 2020-11-01
> **kenbright said:**
>  I gather I need to purge the sources list? but don't know how to go about it

If by purge, you mean remove them, no, don't do that. That would make things worse. What that message means is that line 52 in your /etc/apt/sources.list file is malformed, that is, it's in a state that the package manager can't make sense of. A simple edit is probably all that is needed.

Please post the output of this terminal command:

```
cat /etc/apt/sources.list
```

That will show the contents of the sources.list file so that we can see what is wrong. Please enclose the output between BBCode code tags for clarity. There's a link in my sig if you need a guide to using code tags.

---

### Post by ActionParsnip on 2020-11-01
```

cat -n /etc/apt/sources.list

```

Will be clearer

---

### Post by deadflowr on 2020-11-01
> I gather I need to purge the sources list? but don't know how to go about it
No, don't do that.
It says the component is messed up.
the component is the archive related to it such as stable or contrib or main or something else.
With wine repos I think they only have main.
If adding wine repos make sure it's from here: [https://wiki.winehq.org/Ubuntu]("https://wiki.winehq.org/Ubuntu")

And **NOT** from here: [https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa]("https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa")

---

### Post by kenbright on 2020-11-10
Thanks for all the replies. After some hunting around I found that purge was definitely the wrong move and successfully edited etc/apt/sources. All I need to do now is find why I have  a 'no entry' sign in the top bar next to the internet symbol. It doesnt do anything just opens an empty grey box when I click on it. Otherwise everything else is OK I just haven't tried anything else with wine yet.

---

### Post by deadflowr on 2020-11-10
Post back the sources.list output that both coffeecat and ActionParsnip requested.
Also Run
```
sudo apt update
sudo apt upgrade
```
and post the output for that too, please.

---

