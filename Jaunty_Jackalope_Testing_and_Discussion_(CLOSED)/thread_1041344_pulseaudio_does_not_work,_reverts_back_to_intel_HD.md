---
title: "pulseaudio does not work, reverts back to intel HDA analog (kubuntu)"
date: 2009-01-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tedrampart on 2009-01-16
running since daily build from a few days ago, with all the latest updates installed. (64bit version)

I have sound, but I can't adjust the volume, which is just barely noticable in a silent room (have an intel ICH7 family).

kmix either crashes, or is empty and doesn't show on the panel (no sliders or devices assigned to it), and in the setting, when I test pulse audio I get an error saying "audio device pulseaudio does not work, falling back to HDA intel (ACL262 analog)."

also, when starting stopping restarting /etc/init.d/alsa-utils I get errors, which say: ```
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0                        
amixer: Mixer attach hw:0 error: No such file or directory                             
ALSA lib conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so    
``` over and over, then ```
Invalid card number.                                                                   
Usage: amixer <options> [command]                                                      
Available options: ....(shows all options)
``` for a few pages worth of lines.

seems alsa can't find pulse, or the HDA intel card, but kde sees it and uses it exclusively.  am I right, or way off?  anyone else share this issue?

I'm not sure how to proceed, and all the stuff I've seen relates to gnome.  

this is also my first try at kde (though I used it years ago).. which has got me hooked, great stuff 4.2 is..

---

### Post by Eclipse. on 2009-01-16
Please make a bug report on launchpad and provide as much information as you can to try and help the developers fix this problem.

Thanks

---

### Post by Slug71 on 2009-01-16
> **tedrampart said:**
> running since daily build from a few days ago, with all the latest updates installed. (64bit version)

I have sound, but I can't adjust the volume, which is just barely noticable in a silent room (have an intel ICH7 family).

kmix either crashes, or is empty and doesn't show on the panel (no sliders or devices assigned to it), and in the setting, when I test pulse audio I get an error saying "audio device pulseaudio does not work, falling back to HDA intel (ACL262 analog)."

also, when starting stopping restarting /etc/init.d/alsa-utils I get errors, which say: ```
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0                        
amixer: Mixer attach hw:0 error: No such file or directory                             
ALSA lib conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so    
``` over and over, then ```
Invalid card number.                                                                   
Usage: amixer <options> [command]                                                      
Available options: ....(shows all options)
``` for a few pages worth of lines.

seems alsa can't find pulse, or the HDA intel card, but kde sees it and uses it exclusively.  am I right, or way off?  anyone else share this issue?

I'm not sure how to proceed, and all the stuff I've seen relates to gnome.  

this is also my first try at kde (though I used it years ago).. which has got me hooked, great stuff 4.2 is..

Have you tried adjusting them with:

```
alsamixer -Dhw
```

?

---

### Post by tedrampart on 2009-01-16
gives me:
```
$ alsamixer -Dhw
ALSA lib conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw

alsamixer: function snd_ctl_open failed for hw: No such file or directory

```

---

### Post by Slug71 on 2009-01-16
> **tedrampart said:**
> gives me:
```
$ alsamixer -Dhw
ALSA lib conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw

alsamixer: function snd_ctl_open failed for hw: No such file or directory

```

Thats really weird becasue i also have Intel HDA Analog. ALC268.

---

### Post by tedrampart on 2009-01-16
hmm, it must be something from a bad update or perhaps I got the daily build from the wrong time.. I guess I can wait until the beta's out for sound and try it again if no one has any idea how to fix this.

maybe I'll just install kde 4.2 in ibex vanilla on my other partition to satisfy my new found kde addiction.

---

### Post by Slug71 on 2009-01-16
Try Alpha 3.

---

### Post by tedrampart on 2009-01-16
would it make much difference to install alpha 3 off a disc over installing updates?  heh, I guess it would if you have the same card and it works fine..

---

### Post by Slug71 on 2009-01-16
It could as you would have a hardware configuration during installation.

---

### Post by tedrampart on 2009-01-16
thats a good point, I just downloaded alpha 3, so I'll give that a try, .. if its fixed via that I'll post it up (which I bet it will)

---

### Post by ShirishAg75 on 2009-01-16
It should actually be something like :-

```


$ alsamixer -D hw:0

```

some number like 0 or 1 (if you have more than card) is important at the very end. 

This works for me.

---

### Post by tedrampart on 2009-01-16
nope, same error, I'm going to try the alpha 3 disc and if that fixes it, I'll know its a problem with my install. 

It must be that, since this card has worked for as long as I can remember (dapper or earlier if I remember right)

---

### Post by tedrampart on 2009-01-17
follow...  installed alpha 3.. and now everything works correctly.. so it musta been a bad day to get a build when I did..

thanks for the help all..

---

### Post by caryb on 2009-01-17
I still have the problem with 16/1/09 build:confused: Upgrades have not fixed it


Cary

---

### Post by Slug71 on 2009-01-17
> **tedrampart said:**
> follow...  installed alpha 3.. and now everything works correctly.. so it musta been a bad day to get a build when I did..

thanks for the help all..

Congrats.

---

