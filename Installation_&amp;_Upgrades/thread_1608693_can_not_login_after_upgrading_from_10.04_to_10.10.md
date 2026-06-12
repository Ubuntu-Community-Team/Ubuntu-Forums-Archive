---
title: "can not login after upgrading from 10.04 to 10.10"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by awinw on 2010-10-29
My other PC was upgraded from 10.04 to 10.10 yesterday online.
immediately after upgrading, while re-starting
I can not see  login window,
 always a text screen with "tty1"
 awin-desktop: login:
  password: 
when I login and give the password
there is "Welcome to Ubuntu 10.10"
but then "awin-desktop: ~$ "

and then I can NOT get out of this "terminal" tty1
and can NOT login to desktop

P.S. previously, my 10.04 works quite well.
      when starting 10.04,
       computer will automatically skip the tty1 screen
      and go to normal login window. but not now

what is wrong?  please help,  with thanks

---

### Post by mightysween on 2010-11-02
There are a few other threads on this issue offering various suggestions, depending on your particular situation...



[http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=ubuntu+studio+10.10+login+tty1#hl=en&q=+site:ubuntuforums.org+ubuntu+studio+10.10+login+tty1&sa=X&ei=NXvQTJ_FEYK78gbk_6CmBw&ved=0CBgQrQIwAA&fp=ddfbf15c2e2f4021]("http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=ubuntu+studio+10.10+login+tty1#hl=en&q=+site:ubuntuforums.org+ubuntu+studio+10.10+login+tty1&sa=X&ei=NXvQTJ_FEYK78gbk_6CmBw&ved=0CBgQrQIwAA&fp=ddfbf15c2e2f4021")

On my particular system the problem was related to my video driver settings (Nvidia)and the solution was as simple as completely deleting my xorg.conf file with this command:

sudo rm /etc/X11/xorg.conf

...followed by a reboot.

This forced my video back to the default mode, and I was able to then reinstall the latest Nvidia driver and correctly configure it.   The computer now boots correctly as it had in 10.04 previously.

---

### Post by awinw on 2010-11-03
> **mightysween said:**
> There are a few other threads on this issue offering various suggestions, depending on your particular situation...



[http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=ubuntu+studio+10.10+login+tty1#hl=en&q=+site:ubuntuforums.org+ubuntu+studio+10.10+login+tty1&sa=X&ei=NXvQTJ_FEYK78gbk_6CmBw&ved=0CBgQrQIwAA&fp=ddfbf15c2e2f4021](http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=ubuntu+studio+10.10+login+tty1#hl=en&q=+site:ubuntuforums.org+ubuntu+studio+10.10+login+tty1&sa=X&ei=NXvQTJ_FEYK78gbk_6CmBw&ved=0CBgQrQIwAA&fp=ddfbf15c2e2f4021)

On my particular system the problem was related to my video driver settings (Nvidia)and the solution was as simple as completely deleting my xorg.conf file with this command:

sudo rm /etc/X11/xorg.conf

...followed by a reboot.

This forced my video back to the default mode, and I was able to then reinstall the latest Nvidia driver and correctly configure it.   The computer now boots correctly as it had in 10.04 previously.
-----------------------------
In my scenario, firstly I failed to login after upgrading to ubuntu 10.10, 
                                     but only able to go to terminal tty1 in recovery mode

   secondly, I re-installed my previous 10.04,

thus, my question: 

How can I know this " /etc/X11/Xorg.conf " belongs to  the failed  ubuntu 10.10?
I am afraid of deleting the file in my newly re-installed 10.04.
thanks

---

