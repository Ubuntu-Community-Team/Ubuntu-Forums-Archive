---
title: "Firefox-3.0 Installation Failed"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by Daddyo-613 on 2008-06-20
Hardy Heron 8.0 - Linux version 2.6.24-19-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 4 16:35:01 UTC 2008

I had Mozilla Firefox 2.0.0.14 running fine but I couldn't leave it alone. I had to try to upgrade to 3.0. Now Firefox won't start. I'd like to do a clean install.

I tried removing all installed firefox-3.0 files logged off and returned and did "sudo apt-get install firefox-3.0". It appeared to work in the terminal (ie no error messages) but when I go to launch Firefox I get the firefox crash reporter dialog screen.

Can someone direct me to a how-to for complete removal and a clean install?

Thanks much

---

### Post by z0mbie on 2008-06-20
```
sudo aptitude --purge remove firefox-2 firefox-3.0
```

Also delete the hidden **.mozilla** folder from your home directory.

---

### Post by aysiu on 2008-06-20
By what method did you try to upgrade to 3.0?

P.S. Do *not* delete the hidden .mozilla folder in your home directory. That's where your bookmarks and other settings live.

---

### Post by Daddyo-613 on 2008-06-20
I followed your suggestion but no joy.

Anything else I can try?

---

### Post by aysiu on 2008-06-20
> **Daddyo-613 said:**
> I followed your suggestion but no joy.

Anything else I can try?
Yes, but first you have to explain by what method you had previously tried to upgrade to 3.0.

---

### Post by Daddyo-613 on 2008-06-20
To Aysiu...sorry my previous post was in response to z0mbie's suggestion...I had not seen your post. The following is the sequence I followed to create the problem:

cp -R ~/.mozilla ~/.mozilla.backup
sudo tar -jxvf firefox-3.0.tar.bz2 -C /opt 
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/firefox/plugins /opt/firefox/plugins

sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox

sudo ln -s /opt/firefox/firefox /usr/bin/firefox

I hope that helps.

---

### Post by aysiu on 2008-06-20
That sequence should work. Did you get any error messages when you pasted those commands? Can you post the output of these commands, too? ```
ls /usr/bin/firefox -l
ls /opt/firefox/plugins -l
``` Also, can you try running these commands and seeing if you still get a crash when Firefox starts? ```
mv ~/.mozilla ~/.mozilla.notworking
/opt/firefox/firefox &
```

---

### Post by Daddyo-613 on 2008-06-23
To aysiu;

I've been away. I ran the code you suggested above and the results are below:

```
~$ ls /usr/bin/firefox -l
lrwxrwxrwx 1 root root 20 2008-04-18 13:39 /usr/bin/firefox -> /opt/firefox/firefox

~$ ls /opt/firefox/plugins -l
lrwxrwxrwx 1 root root 24 2008-06-20 15:10 /opt/firefox/plugins -> /usr/lib/firefox/plugins

~$ mv ~/.mozilla ~/.mozilla.notworking
~$ /opt/firefox/firefox &
[1] 6236
~$ (crashreporter:6262): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(crashreporter:6288): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

[1]+  Exit 1                  /opt/firefox/firefox

```

If you're still interested I'd appreciate any suggestions you may have.

---

### Post by aysiu on 2008-06-23
I'm not familiar with that error. I popped it into a Google search and found out [you're not alone](http://support.mozilla.com/tiki-view_forum_thread.php?comments_parentId=80106&forumId=1), but I didn't find any solutions.

---

### Post by Daddyo-613 on 2008-06-23
Misery always loves company.

Sometime prior to trying to upgrade to 3.0 I followed the "sticky" how-to guide to enhance Mutimedia & Video

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

It worked fine by the way but I wonder if something in there may have changed the standard locations of critical files? 

It's just a thought. Clearly, if a clean install doesn't work after a purge, either something has been removed or relocated that the install expects to be there or something has been added that conflicts with the install.

Well, I do appreciate the help. If something else occurs to you please let me know.

---

### Post by Daddyo-613 on 2008-06-23
The problem now seems to be fixed. I went back to 

[http://www.psychocats.net/ubuntu/firefox#terminal]("http://www.psychocats.net/ubuntu/firefox#terminal")
and followed the commands in this sequence

```

sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm -r /opt/firefox
```

Then I went to the directory to where I had downloaded my firefox-3.0.tar.bz2 and executed the following sequence of commands

```

sudo tar -jxvf firefox-3.0.tar.bz2 -C /opt
rm firefox-3.0.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/firefox/plugins /opt/firefox/plugins
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

This time it worked and Firefox 3.0 started up without the error messages. My bookmarks are gone, but, I had previously done a purge and complete removal so that's not a problem. One of life's little mysteries solved.

:)

---

