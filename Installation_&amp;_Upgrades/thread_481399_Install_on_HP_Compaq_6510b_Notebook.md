---
title: "Install on HP Compaq 6510b Notebook"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by xofs on 2007-06-22
Hi all,
I've been using Ubuntu on my desktop since v6.
I just got a HP Compaq 6510b Notebook and the 7.04 CD and am trying to install without luck.

It errors to the shell and says it can't setup the X server.  . .and then that's it.

I didn't post exact error messages and all because I googled that previously and no joy with the stuff I found.

My question here is: Does anyone else out there have the HP Compaq 6510b notebook and got 7.04 installed?

(I hope so. SuSE then Unbuntu have been my main work environment for quite some time and I'm not loving the Vista (especially since sleep blue screens it). Not bashing the big V, that is just what is happening. 

Thanks!

---

### Post by mwiertz on 2007-07-01
Hi,

I've bought the same laptop/notebook from HP myself. And of course I ran into the same problems as you experienced.

But I managed to get Ubuntu installed and booting. Here's what I did:

As the LiveCD did not work, I downloaded the Alternate install cd and installed from that disc in text mode. Ok, it look sa little old fashioned, but it works just as good as the more fancy GUI installer.

Afterwards my notebook booted up, but was not able to start the X server environment.

So I booted the alternate installer cd again, but now I chose the repair/recovery mode. I made all the settings for the locale, keyboard layout and things. I mounted my root ("/") partition. And last but not least I started a shell in my root environment.

In that shell I used the following command sequences:
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install xserver-xorg-video-intel

After that I rebooted the system, just normally from the harddisk, and it started without any problems.

Hope this helps, regards
Max

---

### Post by jferna57 on 2007-07-04
Thank you for the information. I resolve my problem.

Now, i have problems with cd-dvd.

Can you help me?

---

### Post by mwiertz on 2007-07-04
Hi,

Excuse me for my late reaction, I have been on a business trip for a few days, so I was not in a position to answer your question...

Anyway, unfortunately I cannot answer your question at the moment. But I'm downloading an iso image right now, so I can tell you tomorrow if I am able to burn on cd/dvd. Reading cd's is no problem btw.

But what I would like to ask you is if you experience something strange with the display too. I always think the fonts and borders etc are not sharp and I also have the feeling that I'm running the wrong colourdepth mode. Although it is set to 24 bit. The standard ubuntu background for example shows a little bit blocked, like a zoomed in bitmap graphic. Do you recognize this too?

thanks

---

### Post by xofs on 2007-07-06
Thanks x3 for the info!

I now have Ubuntu running nicely on the 6510b!

I somehow managed to screw up the instructions you posted but after poking around the X11 directory, I found:

sudo dpkg-reconfigure -phigh xserver-xorg

and set the chipset to Intel and the resolution to 1280x800

and now it all works great!

(haven't tried cd burning; just happy to have my normal toos/environment)

Thanks again!

---

### Post by xofs on 2007-07-06
One more thing on the display.
Not sure the depth
but I have X set to 1280x800 (intel)
and the screen is beautiful and sharp--no issues there.

---

### Post by mwiertz on 2007-07-07
Hi,

in the meanwhile I discovered that cd drive does not work too, the one I got working was my external USB drive (sorry for that)...

But there seems to be a solution. You can use some generic-ide driver for non-dma access.

Just take ahead and look into this thread:
[http://ubuntuforums.org/showthread.php?t=481651](http://ubuntuforums.org/showthread.php?t=481651)

It also told me there has been released a new video driver:
[http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943)

hope this helps...

---

### Post by Snafuc on 2007-07-13
Hi!
I'm very interested in the HP 6510b but there still seem to be some problems to get linux (esp. ubuntu) running fine on it.
Can anyone post how things are going on as I'd like to buy that notebook if things are working fine.

Cheers

---

### Post by Snafuc on 2007-07-20
bump

---

### Post by dptd on 2007-09-15
First of all i want to say "thank You" because only because of You i managed to run Ubuntu on my HP Compaq 6510b!! :)

But ... i have another problem/question. Why I have only 16bit dept color? On my wallpaper I see pixels when colors changes etc. Can anyone help me?

I'm a newbie in linux systems (Ubuntu also ;)) so If somebody know how can I fix this graphic problems please write this step by step.

Thx. :)

---

### Post by jimbob on 2007-09-15
Are you sure you are not confusing 16-bit depth with 16 million colors at depth 24?
 Post a copy of your /etc/X11/xorg.conf file.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

