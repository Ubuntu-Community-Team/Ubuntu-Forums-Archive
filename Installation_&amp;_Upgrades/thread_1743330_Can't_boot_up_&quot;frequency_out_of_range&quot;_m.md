---
title: "Can't boot up &quot;frequency out of range&quot; message appears on the screen"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by bvil on 2011-04-29
I upgraded 10.10 to 11.04 last night, and after it restarted, the message,"frequency out of range," popped up and can't even log in. Any suggestions?

---

### Post by ghormax on 2011-04-29
My computer boots well (I have a clean install of 11.04) but during the boot and shutdown, the frequency is also out of range. What could be the problem?

---

### Post by sikander3786 on 2011-04-29
What is the native resolution of your monitor?

---

### Post by bvil on 2011-04-29
mine is 1440x900

---

### Post by dmgroom on 2011-04-29
Sorry as I'm not very technical, but I had the same problems this moring and solved it as follows:

At the point where you would be expecting to see a GRUB menu hit the "down arrow" key, followed by "enter/return" key.  This should get you in to the recovery mode option of the grub menu.

From the next menu choose "run in failsafe graphics mode".

If you have not already installed the start up manager then install it from synaptic package manager (search for "startupmanager").

Then choose System > Administration > StartUp-Manager

Under both "boot options" and "advanced" tabs choose a resolution and colour depth that your monitor supports.  save these settings and rebbot.

---

### Post by bvil on 2011-04-29
I just tried it a couple of times and couldn't even get to GRUB menu. The first time it went to memory test and the other times it seemed like loading something as it was shown on the screen but it kinda froze right after.

---

### Post by Fervid on 2011-04-29
You can either wait until you think GRUB has loaded and press down once, then enter and you will probably get to recovery. If not, boot from the live CD and edit:

/etc/default/grub
uncomment the line:
```
#GRUB_TERMINAL=console
```Save the file then run
```
sudo update-grub
```Once it is complete you can reboot and you should be able to see your grub menu.

---

### Post by RJARRRPCGP on 2011-04-29
The problem probably is the resolution being set too high.

---

### Post by Hedgehog1 on 2011-04-30
Hi Folks!  This one has come up a lot. Please do this:

```
gksudo gedit /etc/default/grub
```

[COLOR="Red"]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR="red"]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR="red"]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```


***The Hedge***

:KS

---

### Post by bvil on 2011-04-30
this screen popped up after trying to get to the recovery menu. I have no idea what that means but I'm guessing the installation wasn't somehow completed? And I'm sorry I'm a absolute noob, what do you mean by uncomment the line?

---

### Post by Hedgehog1 on 2011-04-30
> **bvil said:**
> this screen popped up after trying to get to the recovery menu. I have no idea what that means but I'm guessing the installation wasn't somehow completed? And I'm sorry I'm a absolute noob, what do you mean by uncomment the line?

bvil - this is a very different issue.  Please start a fresh thread with this - thanks!

***The Hedge***

:KS

---

### Post by bvil on 2011-04-30
> **Hedgehog1 said:**
> bvil - this is a very different issue.  Please start a fresh thread with this - thanks!

***The Hedge***

:KS

I'm sorry, will do. Thanks for the help!

---

### Post by Fervid on 2011-04-30
To uncomment means to remove the # from the beginning of a line. Any line prefaced with # is ignored.

I had the same issue as you are having but on a cheap little emachine desktop (the ones that Best Buy sells for $300 or so) and changing the resolution as hedgehog suggested didn't help. Forcing grub to a lower resolution might fix the original issue for you though. If not the fix I posted will at least let you see grub.

Not booting at all is another issue though :(. I'll look for your other thread and see if I can help.

---

### Post by bvil on 2011-04-30
I've tried both methods but neither worked. 
```

ubuntu@ubuntu:~$ gksudo gedit /etc/default/grub

(gedit:6482): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.3HKWUV': No such file or directory

(gedit:6482): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:6482): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.XWNWUV': No such file or directory

(gedit:6482): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot stat `aufs'.
```

here's my other thread 
[http://ubuntuforums.org/showthread.php?t=1744759](http://ubuntuforums.org/showthread.php?t=1744759)

---

### Post by bitzbox on 2011-05-01
> **dmgroom said:**
> Sorry as I'm not very technical, but I had the same problems this moring and solved it as follows:

At the point where you would be expecting to see a GRUB menu hit the "down arrow" key, followed by "enter/return" key.  This should get you in to the recovery mode option of the grub menu.

From the next menu choose "run in failsafe graphics mode".

If you have not already installed the start up manager then install it from synaptic package manager (search for "startupmanager").

Then choose System > Administration > StartUp-Manager

Under both "boot options" and "advanced" tabs choose a resolution and colour depth that your monitor supports.  save these settings and rebbot.

I was having exactly the same problem until I read your post. 
I followed your instructions and the problem is now solved. 
Thank you very much indeed for posting your solution.

Worked for me! :biggrin:

---

### Post by andy_blah on 2011-05-10
I've been having this problem ever since I updated the kernel version and reinstalled the video drivers. It happens after grub and before I log in with my account. I tried running:
```
sudo dpkg-reconfigure xserver-xorg
```

as some forums/threads pointed, but it just returns a blank line and nothing happens (the threads were quite old since I couldn't find anything recent so I suppose it's outdated). So then, what do I do? X.X

Also I don't get the choice for starting in failsafe graphics mode after GRUB, so am I doing something wrong here? ~.~

---

### Post by andy_blah on 2011-05-10
*bump* Seems that all my questions get ignored lately

---

### Post by Hedgehog1 on 2011-05-11
> **andy_blah said:**
> *bump* Seems that all my questions get ignored lately

As a practical matter, attaching a question to the end of a week old thread mean most of us will never see your question.  This may explain your poor response rate.  

Please create a new thread with your issue plainly stated.

Thanks!

***The Hedge***

:KS

---

### Post by andy_blah on 2011-05-11
Why should I create a new thread if I have the same problem as the guy who started it? ~.~
But whatever, I'll go do that.

---

### Post by MAFoElffen on 2011-05-11
> **bvil said:**
> this screen popped up after trying to get to the recovery menu. I have no idea what that means but I'm guessing the installation wasn't somehow completed? And I'm sorry I'm a absolute noob, what do you mean by uncomment the line?
" # " -- See the pound character inside my quotation marks at the left? In Linux, that is a comment character, meaning that things to the right of it are a comment or not seen.

If you delete the # character, anything after will be seen.  In what Hedgehog1 asked you to do was to delte that comment character, so that that line will be seen and execute.

I'm in aggreement wit Hedghog1, plus an additional comment... There are actually 3 parameters for GFXMODE instead of 2. (Its buried in the GNU and Xorg Doc's)
```

GFXMODE=*WIDTH*x*HEIGTH*x*DEPTH*

```At default, GFXMODE is set to "auto"... meaning, it tries to query and find a valid mode.  This "IS" where most of these black screens are occurring.  Now if you set the HEIGTH and WIDTH, it's still going to query for the DEPTH's... See where that's going?

So if you set it to a known Resolution such as
```

GFXMODE=640x480x24

```

---

### Post by danrael on 2012-05-21
[COLOR="Indigo"]I solved the issue via **Grub Customizer[COLOR="DarkRed"]*[/COLOR]**.  First, you will need to boot into Ubuntu by hitting 'Enter' at the 'out of range' message:[/COLOR]

[COLOR="DarkRed"]Since Ubuntu 11.04 Natty, after a fresh Ubuntu installation on my desktop PC, the monitor starts into **[COLOR="Black"]&#8216;input signal out of range Change Settings to **x** 60HZ&#8217;[/COLOR]**.

The problem can be fixed by resetting the Grub screen resolution ratio. I used to use Startup-Manager, but &#8216;StartUp-Manager is dead&#8217; it has been dropped in Ubuntu 12.04&#8242;s repository.

In Ubuntu 12.04 LTS, we can use **Grub Customizer** to fix the problem:

    1. Start your machine, on &#8216;signal out of range&#8217; screen press **Enter**. Wait a few seconds (or try Ctrl+Alt+F1, Ctrl+ALt+F7), it will boot into Ubuntu.

    2. Once booted into Ubuntu, configure the network and install **Grub Customizer** by running following commands in terminal:[/COLOR]

    [B]sudo add-apt-repository ppa:danielrichter2007/grub-customizer
    sudo apt-get update
    sudo apt-get install grub-customizer[/B]

   [COLOR="DarkRed"] Or directly download and install the deb from launchpad.net

    3. Launch **Grub Customizer** from **System>Grub Customizer**.

In its **Preference** window second tab, check and change the resolution. Remember to click &#8216;Save&#8216; the configuration:[/COLOR]

[IMG]http://ubuntuguide.net/wp-content/uploads/2012/04/grub-customizer-500x313.png[/IMG]
*****

**[COLOR="Indigo"]At first, I could not get this to work with a setting of 1024x768, but at 800x600x16 it all worked out.  I suggest experimenting with the settings that work to get the best resolution.[/COLOR]**

[COLOR="Indigo"]*The original post is found here:[/COLOR]

[http://ubuntuguide.net/monitor-signal-out-of-range-problem-in-ubuntu-12-04-precise-fresh-installation](http://ubuntuguide.net/monitor-signal-out-of-range-problem-in-ubuntu-12-04-precise-fresh-installation)


[COLOR="Navy"]
Reader Comments

Awesome thanks ever so much.

Bill

[Reply]
#1 
Written By Bill on April 27th, 2012 @ 12:37 pm

Sorted this problem out for me too. Thanks a lot!

[Reply]
#2 
Written By Paul on April 30th, 2012 @ 1:38 pm

How do I do this if I don&#8217;t have access to the Ubuntu GUI?

[Reply]

admin Reply:
May 1st, 2012 at 7:40 pm

Manually edit the grub:

**sudo nano /etc/default/grub**

find this line:
**#GRUB_GFXMODE=640x480**

remove the # and change 640×480 for the preferred mode you wrote down.

save, then type

**sudo update-grub**

[Reply]
#3 
Written By Robert on May 1st, 2012 @ 6:21 am

Thanks for this, was banging my head against the wall trying to figure out where StartUp-Manager had gone.[/COLOR]
*****

---

### Post by oldos2er on 2012-05-21
Old thread closed.

---

