---
title: "upgrade flag"
date: 2017-04-17
forum: Installation &amp; Upgrades
---

### Post by dyk on 2017-04-17
Hello everybody, some weeks ago I've upgraded my 12.04 LTS server version with the 17.04 version but the warning: "Ubuntu 12.04 LTS end-of-life is April 25, 2017 -- Upgrade your Precise systems!" doesn't disappear.

I've checked with lsb_release and the version is "zesty", I've tried with "ubuntu-support-status" but I've this error:" Traceback (most recent call last):  File "/usr/bin/ubuntu-support-status", line 149, in <module>
    'time' : time})
TypeError: not enough arguments for format string
"

Any suggestion?

Thank you...

---

### Post by mjonker83 on 2017-04-18
Hello,

I had the same issue but found that the file /etc/update-motd.d/50-motd-news was the one giving the message. This file gets some information out of /etc/default/motd-news and that file gets the text from an URL ( [https://motd.ubuntu.com](https://motd.ubuntu.com) ).
I removed the file /etc/update-motd.d/50-motd-news and now I do not get the message anymore.

Hope this will give you some information on how to disable the message.


> **dyk said:**
> Hello everybody, some weeks ago I've upgraded my 12.04 LTS server version with the 17.04 version but the warning: "Ubuntu 12.04 LTS end-of-life is April 25, 2017 -- Upgrade your Precise systems!" doesn't disappear.

I've checked with lsb_release and the version is "zesty", I've tried with "ubuntu-support-status" but I've this error:" Traceback (most recent call last):  File "/usr/bin/ubuntu-support-status", line 149, in <module>
    'time' : time})
TypeError: not enough arguments for format string
"

Any suggestion?

Thank you...

---

### Post by gut2 on 2017-04-18
> **mjonker83 said:**
> Hello,

I had the same issue but found that the file /etc/update-motd.d/50-motd-news was the one giving the message. This file gets some information out of /etc/default/motd-news and that file gets the text from an URL ( [https://motd.ubuntu.com](https://motd.ubuntu.com) ).
I removed the file /etc/update-motd.d/50-motd-news and now I do not get the message anymore.

Hope this will give you some information on how to disable the message.
I'd not remove a system file. Possibly disabling the notifier would be a better idea (edit the /etc/default/motd-news file and change it).

I guess something didn't go smooth as Ubuntu planned for this update. There will be a better solution to this...

---

### Post by Impavidus on 2017-04-18
> **gut2 said:**
> I guess something didn't go smooth as Ubuntu planned for this update. There will be a better solution to this...

Which upgrade? 12.04 LTS &#8594; 14.04 LTS &#8594; 16.04 LTS &#8594; 16.10 &#8594; 17.04 looks like four upgrades to me. If you used loopholes to skip some intermediate releases, then you used an upgrade that was never planned, so no surprise it's not very smooth.

For what it's worth, on my Xubuntu 16.10 system (I will upgrade in a few weeks) there is neither a /etc/update-motd.d/50-motd-news nor a /etc/default/motd-news file. And this was a clean install of 16.10.

---

### Post by gut2 on 2017-04-18
> **Impavidus said:**
> Which upgrade? 12.04 LTS &#8594; 14.04 LTS &#8594; 16.04 LTS &#8594; 16.10 &#8594; 17.04 looks like four upgrades to me.

My case is directly from a 16.10 -> 17.04 and I have the same output when logging in:
```
Welcome to Ubuntu 17.04 (GNU/Linux 4.10.0-19-generic ppc64le)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage


Ubuntu 12.04 LTS end-of-life is April 25, 2017 -- Upgrade your Precise systems!
 $ sudo do-release-upgrade -m server
```

This system was never 12.04 but it still warns me.

---

### Post by grahammechanical on 2017-04-18
It gets confusing if more than one person is looking for support in the same thread. I have just been confused with what dyk said in the first post and what gut2 said in his/her second post.

It could be that the server team are being extra diligent in make sure that users of the Ubuntu 12.04 server do not end up running an unsupported system.

Regards.

---

### Post by gut2 on 2017-04-19
> **grahammechanical said:**
> 
It could be that the server team are being extra diligent in make sure that users of the Ubuntu 12.04 server do not end up running an unsupported system.

Interesting. Let's wait until 26th April and see if it goes away.

---

### Post by gut2 on 2017-04-26
nope, it's still there :(

---

