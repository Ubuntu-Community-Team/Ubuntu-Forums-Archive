---
title: "Launch Bar &amp; DVD Watching Issues"
date: 2014-03-22
forum: Installation &amp; Upgrades
---

### Post by Jay_N on 2014-03-22
Hi,

While I'm not new to Ubuntu, I'm new to this forum. I'd be glad to help or be helped! 
I'm wondering if I can upgrade from unity 2D to Unity 3D? I want to be able to change the launch bar size. 
Does Ubuntu 12.04 LTS use Gnome or Unity? 

I'll explain why - I installed the Nvidia drivers thinking that it would allow me to play DVDs on my computer. I had already installed the codecs to no avail and the Nvidia drivers didn't help any. (Removed the Nvidia drivers after).
But after that my launch bar was back to being large icons and I can't remember how I made them smaller to begin with. I have unity 2d installed and can't adjust the launch bar icons using the slider since I don't have that option. 

But now if I want to move my launch bar up or down I have to manually scroll it up or down using my mouse wheel. Also, the trash icon seems to be fixed at the bottom and doesn't move with the rest of the launch bar. 
I'd like to know how to solve this issue. 

If anyone also knows how to watch DVDs which I was originally trying to do, that would be helpful too.

---

### Post by Kirboosy on 2014-03-24
Ubuntu 12.04 comes with Unity. Unless you download a alternate desktop environment. 

When setting up for DVD play did you follow this guide? [RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") I have never had an issue with DVDs playing properly under Ubuntu using that guide.

Hope that helps!
~Caboose

---

### Post by Jay_N on 2014-03-27
I've tried with no success to play a DVD. I followed the guide and I still get this message.
'Could not read DVD. This may be because the DVD is encrypted and a DVD decryption library is not installed.'

I've tried different DVD's as well. 

I have the Ubuntu Restricted Extras installed, I also have libdvdcss2 and libdvdread4 installed.

Not too sure what else to do.

---

### Post by Kirboosy on 2014-03-28
What media player are you using? I have used VLC with no problems but it just occurred that another media player might have issues.

---

### Post by Jay_N on 2014-03-29
I have tried Media Player (Totem I think) and VLC with no luck. 
I also tried to install libavcodec-extra-53 because I saw it was part of the files for libdvdread4 or libdvdcss2. But when I right click on the file and choose 'Open With Ubuntu Software Center' it says 'Cannot install libgsm1:i386
Regular videos will play if I have them on the computer but not DVDs so I'm thinking it's some kind of decryption issue.

---

### Post by Kirboosy on 2014-03-31
Perhaps this guide will help you change the icon size back to the way you had it before?

[Changing Icon Size Unity 2D]("http://ubuntuforums.org/showthread.php?t=1943423")

What version of Ubuntu 12.04 are you using? 32 Bit or 64 Bit?

Hope that helps!
~Caboose

---

### Post by Jay_N on 2014-03-31
Hi Caboose,

Thanks for the help so far. I'm running Ubuntu 12.04 64 bit.
I know that DVD's will play in this computer because I have a dual boot with winblows and I can play DVD's there. So it must be some kind of codec issue. 
I did figure out though that somehow I had started unity 2d instead of unity 3d. I assume it's 3d (it just says unity in the menu) because I can change the launch bar size and my launch bar issue is fixed. 
Still can't play DVD's though.

---

### Post by grahammechanical on 2014-03-31
Ubuntu 12.04 uses both Gnome and Unity. It uses the Gnome desktop environment and the Unity user interface. Unity 3D is installed as the default unless our graphic adapter cannot run Unity 3D then with 12.04 Unity 2D (which uses Metcity and not Compiz as the window compositor) gets installed. So, if you do not have the option at the login screen to choose either Ubuntu or Unity 2D then may be you do not have Unity 3D on your system. This is the command to test for Unity 3D support.

```
/usr/lib/nux/unity_support_test -p
```

You could also try

```
unity --reset-icons
```
```
setsid unity
```
```
dconf reset -f /org/compiz
```

Regards.

---

### Post by Kirboosy on 2014-04-01
After you installed the packages you ran the following command right?

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

*Note some people report needing to reboot after running the script for it to work properly.

At this point I'm out of ideas. I don't understand why it won't work for you. 

I don't think its due to regions either because it works fine in Windows. What player are you using in Windows?

~Caboose

---

### Post by Jay_N on 2014-04-01
Hi Caboose,

Thanks for all your help. I've made DVD playing progress!! To answer your question, I use VLC or Winblows Media Player, but I only kept winblows so I could use cakewalk sonar music editing program. . I tried that line of code you gave me again, and noticed that it said libdvdcss2 wasn't compatible with libdvdcss. I removed libdvdcss2 and ran the code you gave me again and then tried a DVD and it worked!! 

Thanks to you for helping me solve my issue.

---

### Post by Jay_N on 2014-04-01
Hi Grahammecanical,


Thanks for the info. I realized i was using unity 2d. It must have changed when I was trying to install the nvidia drivers. I have since removed them and stuck with the ubuntu graphics driver. I switched back to unity 3d and everything works fine now!![**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323")

---

### Post by Jay_N on 2014-04-01
I'm not sure how to mark this thread as solved now.

---

### Post by BlinkinCat on 2014-04-01
> **Jay_N said:**
> I'm not sure how to mark this thread as solved now.


Hi,

Here's how - [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :)

---

### Post by Kirboosy on 2014-04-02
Well, I'm glad its working. Just when I ran out of ideas the silly thing started working. :lol:

Glad to have helped!
~Caboose

---

