---
title: "How To nVidia restricted drivers in Lucid 10.04"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by 2hot6ft2 on 2010-05-04
I have nVidia cards in all my machines. Needless to say it drove me nuts at first. But it's working great now.
I'm installing the 64 bit. I don't think it matters which kernel you use to do it if you're running 32 bit..
It should work with future kernels but wont know until we get some new ones.

So for everyone's benefit, here's how I ended up doing it and it working with both kernels and where the info. came from.. 
Thanks go to TheeMahn, bpollen and  BlackWolf
(In no particular order).

I found it in this thread. :lol: 
[http://forumubuntusoftware.info/viewtopic.php?f=68&t=4584](http://forumubuntusoftware.info/viewtopic.php?f=68&t=4584)
and did this as recommended by TheeMahn and BlackWolf:

Boot into the second kernel which was
2.6.32-21
NOT 2.6.32-22
Installed the driver (when it said one was available by clicking on the panel applet).
You could also do it from
System > Administration > Hardware Drivers
and reboot choosing the 21 kernel again.

Then you can reboot to either kernel and it will work. Seriously.
If you followed other guides and removed programs, blacklisted things and made all kinds of changes your best bet is to re-install and follow those simple steps.

No blacklisting anything or removing anything is required.

You can, **if you want to**, remove the 2.6.32-22 kernel from the 64 bit version, and after rebooting go to
System > Administration > Synaptic Package Manager
Click on Refresh then try searching for
2.6.32-22
and it wont find it. Why. Because it's not mainstream yet as of writing this. It was still a proposed release and somehow got into the 64 bit release, it's not in the 32 bit release. The nVidia driver should work just fine with normally released kernel upgrades.

I did have a in depth guide that in increased boot screen resolution here but took it out since you can go to:
System > Administration > StartUp-Manager
And set the resolution there.

Now since everyone was expecting a long guide on what to do here are a few tweaks I did to make things run better in case you're bored now that that's fixed.

Firefox changes

1) Type &#8220;about:config&#8221; (no quotes) in the address bar in the browser.
2) Copy and paste the Preference Name into the Filter
3) For true/false entries right click and select Toggle OR double click on it.
4) For others right click and select Modify
You might have to create some of these entries by Right Click &#8211;> New &#8211;>Integer, String or Boolean in the lower section where the preferences are.

```
Preference Name						Type		Value

config.trim_on_minimize				New ->	boolean		true
browser.blink_allowed					""		false
browser.urlbar.doubleClickSelectsAll			""		true
network.dns.disableIPv6					""		false
browser.search.openintab				""		true
ui.submenuDelay					New ->	Integer		0
browser.sessionhistory.max_total_viewers		Integer		0 (was -1)
network.http.pipelining					boolean		true
network.http.proxy.pipelining				boolean		true
network.http.pipelining.maxrequests			Integer		some number like 10 (was 4)
nglayout.initialpaint.delay			New ->	Integer		0
content.notify.backoffcount			New ->	Integer		5
content.notify.interval				New ->	Integer		0
plugin.expose_full_path					boolean		true

```
Close and reopen firefox.

[Speed up Firefox by moving cache into RAM]("http://ultimateeditionoz.com/forum/viewtopic.php?f=23&t=216")

[quote="Blackwolf"]By default Firefox puts its cache in your home partition.You can speed up Firefox and reduce disk writes by moving this cache into RAM if you have 1GB RAM or more.

1.Edit /etc/fstab,open terminal from Applications->Accessories menu and type:

    ```
sudo gedit /etc/fstab
```

Add following into this file and close it.

    tmpfs /tmp tmpfs noexec,defaults,noatime 0 0
    tmpfs /var/tmp tmpfs noexec,defaults,noatime 0 0

2.Edit /etc/sysctl.conf:

   ```
 sudo gedit /etc/sysctl.conf
```

add this line and save it:

    vm.swappiness=1

3.Type about:config in firefox address bar and click I'll be careful,I promise!.Right click on blank area and create a new string value called browser.cache.disk.parent_directory,set its value to /tmp

Now,reboot your system and experience the performance.:grin:[/quote]

:popcorn:

---

