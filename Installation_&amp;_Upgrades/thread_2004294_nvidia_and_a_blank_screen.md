---
title: "nvidia and a blank screen"
date: 2012-06-15
forum: Installation &amp; Upgrades
---

### Post by Pedroski55 on 2012-06-15
I just installed 12.04 on a friend's laptop with nvidia card. All went well, until the ominous 'you must reboot' 
I cannot now boot into a graphical environment. I have a black screen. Her laptop has a GeForce 7000

So I can't set up the dsl connection.

So I can't install the needed nvidia stuff.

I tried nm-connection-editor from a virtual terminal, but it wants X and gtk.

I tried putting VESA in the boot line of grub. 

Any tips out  there??

---

### Post by bogan on 2012-06-15
Hi!, **Pedroski55**,

Was there a previous version of Ubuntu & a nvidia driver installed?

The 7xxx series card should run without problems with the default driver in 12.04, but see Q3: below.

Q1: At what stage do you get the black screen ? before or after log-in?

Q2: In the black screen does 'Ctrl+Alt+F1' give a tty log-in prompt?

Q3: Clearly you get a grub menu: Have you tried other options in the boot line?

Excerpt from Post #1:
> To try different kernel boot options, using "e" at the grub menu. Go to  the kernel boot line... try these options (one at a time/not together):   
      

        ```
 nomodeset   
 xforcevesa   
 i915.modeset=0
 xforcevesa    
vga=xxx # Note- where xxx is a vesa mode that your card supports, such as 771
``` These options, again, would be added near the end of the line, after the kernel name,  For other boot options, look here: 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)Q5: Can you boot into recovery? If so can you continue normal boot from there? or drop to terminal with Internet connection? - you may need to run the FSCK option first to get the Read/Write setting.

Q6: Have you Internet connection to download the nvidia driver, either from Windows or transferred from another computer?

Chao!,** bogan**.

---

### Post by Pedroski55 on 2012-06-15
Thanks for your reply. 

No, there was no Linux ever installed. It is her first Linux. I thought it would run smoothly. 
After the login, I lose the screen. 
I can login to a virtual desktop with ctrl alt f*
I tried booting into failsafeX, it says, and I quote, 'no screens found'

I will try the options you suggest, and report, thanks!

---

### Post by Pedroski55 on 2012-06-15
Well, I tried xforcevesa. I got the background picture after login, but nothing else. No top task bar, no side task bar, a crippled system. But a right click on the desktop gave me the chance to 'change desktop background' and I was in System Settings, so I went to Proprietary Drivers, and got rid of the nvidia. Now the system works. 

I have downloaded nvidia's own installer. I might try it later. But I have a nasty feeling, nothing will work afterwards!!

---

### Post by Pedroski55 on 2012-06-15
&#8221;or drop to terminal with Internet connection?&#8220;
I would love to know how to boot into a virtual terminal and have my dsl connection there up and running!!

"Better Solutions may bring Worsened Problems": After Lao Tse, b. circa 405BC. a contemporary of Confucius. Died:circa 600BC.
They did things differently in those days, apparently!! 			

This quote clearly shows, Lao Tse used Linux!!

---

### Post by bogan on 2012-06-16
Hi!, **Pedroski5**5,

You Posted:>  I have downloaded nvidia's own installer. I might try it later. But I have a nasty feeling, nothing will work afterwards!!I have two versions of 12.04 on one of my computers with 7xxx nvidia card; a fresh installed version running fully and with no problems with the default Nouveau driver, the other, an updated version originally 9.04 has used each of the sequence of nvidia drivers downloaded up to 295.59.

The latter having no problems other than having to reinstall nvidia after most - though not all - kernal updates. 

So put your mind at rest, whichever way you choose to go.

> I would love to know how to boot into a virtual terminal and have my dsl connection there up and running!! I find that booting to a terminal via recovery mode - after running FSCK and the Internet connect options first - gives me an active wifi connection about one time in three. So I prefer to boot into the gui - at least to the log-in stage, so that the WiFi connects normally, and then use 'Ctrl+Alt+F1' and```
 sudo service lightdm stop
``` to close down the Xserver before download-re-installing the nvidia driver.

If your dsl connection is a dial-up you may need to actively, manually activate it.

Chao!, **bogan.**

---

### Post by Pedroski55 on 2012-06-16
Well thanks again. Busy today, but I'll try tomorrow, and post the result.

As to wifi: my router has wireless. It has the wep2 key printed on it, but it is not possible to connect to it. My laptops can see China-QqNet, and I enter the WEP key, but it never connects.

At school the wireless connects effortlessly to various open networks, so I am ruling out a hardware problem.

Also, Windows can connect at home. But, even if the dsl cable is not plugged in, we have to pretend it is , and click 'connect the dsl network', then wireless will work. I don't know how to do this in Linux!

---

### Post by Pedroski55 on 2012-06-16
Well, after reading a bit, I did this:

went to System Settings > Proprietary Drivers The top one is marked (recommended), but I told it to install the bottom of three, updates testing. 

And that one works!!  So now my favourite wobbly windows work! (Until the next update changes it)

---

### Post by bogan on 2012-06-17
Hi!, **Pedroski55**,

Great!, glad you got it sorted.

Please Post the output of:```
 sudo apt-cache policy nvidia-current
```Chao!, **bogan.**

---

### Post by Pedroski55 on 2012-06-18
Sorry, but potato is Chinese, so the result came out in Chinese, hope it helps!
potato@Potato2012:~$ sudo apt-cache policy nvidia-current
[sudo] password for potato: 
nvidia-current:
  &#24050;&#23433;&#35013;&#65306;  (&#26080;)
  &#20505;&#36873;&#36719;&#20214;&#21253;&#65306;295.40-0ubuntu1
  &#29256;&#26412;&#21015;&#34920;&#65306;
     295.40-0ubuntu1 0
        500 [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) precise/restricted i386 Packages
        100 /var/lib/dpkg/status
potato@Potato2012:~$ 

Thanks for your help.

btw If you mean the Italian word, then that is ciao, as in 'ciao bella'

---

### Post by bogan on 2012-06-18
Hi!, **Perdoski**,

Thanks for the Post.

The 295.40 Nvidia driver installed is the notorious bugged version; but if it works, why change it ?

I have it running OK on one 12.04 LTS installation, though it will not on two others.

BTW. I know the Italians spell it 'ciao', but I learnt to use it in South America 60 years ago where the 'c' is pronounced differently, and it stuck.

Chao!, **bogan**.

---

