---
title: "Problems installing Ubuntu on macbook air"
date: 2014-10-05
forum: Installation &amp; Upgrades
---

### Post by whatamidoingahh on 2014-10-05
Hello I am trying to install Ubuntu on my macbook air. I have partitioned my hard drive and installed rEFit v.0.14 but my problem is the bootable usb drive. I downloaded 

ubuntu-14.04-desktop-amd64+mac.iso and converted it to .img. But when I try to put it on the USB using ```
[COLOR=#110000][FONT=Helvetica Neue][TABLE="width: 100%"]
[TR]
[TD="class: code"][COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**dd**[/COLOR] [COLOR=#007800]if[/COLOR]=[COLOR=#000000]**/**[/COLOR]path[COLOR=#000000]**/**[/COLOR]to[COLOR=#000000]**/**[/COLOR]ubuntu-12.04.1-desktop-amd64+mac.img [COLOR=#007800]of[/COLOR]=[COLOR=#000000]**/**[/COLOR]dev[COLOR=#000000]**/**[/COLOR]rdiskX [COLOR=#007800]bs[/COLOR]=1m[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]

```
I used the correct file path not /path/to I was just lazy to write the file path here.
I get an error message saying "This disk you inserted was not readable by this computer." after a minute or so of it being put on 

I restarted just to see if it would work I got this.
[http://imgur.com/MGxkdOB](http://imgur.com/MGxkdOB)
I tried to go ahead and see what would happen If I loaded up the far right ones and I got this
[http://imgur.com/RamjyMp](http://imgur.com/RamjyMp)

Since these didn't work I wiped the drive and tried to have a Universal USB installer do it for me. But I got an error message saying an error happened and it wouldn't be bootable. I restarted anyway to see if it would show up but nothing was there, just the option to boot from Mac HD or recovery.

This is the error: [http://gyazo.com/8bb32beece1cc650999c2b1c45eb91ca](http://gyazo.com/8bb32beece1cc650999c2b1c45eb91ca)
And this is what the starting screen looks like : [http://imgur.com/z3o9rsj](http://imgur.com/z3o9rsj)

Is it my USB drive? Am I doing anything wrong? I followed the instructions step for step or at least I think i did.

---

