---
title: "Problem with audio configuration at login"
date: 2020-07-20
forum: Installation &amp; Upgrades
---

### Post by rafacalifa101 on 2020-07-20
Hi. This is my first message.
I am writing to see if you can help me with my problem. Uso KUBUNTU 20.04 and as image is worth a thousand words, what I intend to do is fix what appears in [this video]("https://photos.app.goo.gl/iEs1kr71ZoC7QueTA") so that I don't have to do this every time I log in. I apologize if the language of the PULSEADIO application is not understood.
Thanks and regards.

---

### Post by wildmanne39 on 2020-07-20
Hi, I do not think it is clear what the issue is so please use your words and tell us what the exact issue is.

Thanks

---

### Post by rafacalifa101 on 2020-07-21
The problem I have is that when I log in I don't have audio. After doing a lot of research, I have managed to find out that it is because I have to do two things: first, change the internal audio and choose PROFILE: ANALOG STEREO OUTPUT, and secondly, choose PORT: OUTPUT LINE.
All this is what you have to do graphically (according to the video I posted earlier), but I know that it can be done manually through the terminal window, and leave the problem solved, in such a way that at each start Session, there is audio without any problem, and you do not have to repeat the graphic process with PULSEAUDIO.
I do not know if I explained well...

---

### Post by CatKiller on 2020-07-21
> **rafacalifa101 said:**
> I have managed to find out that it is because I have to do two things: first, change the internal audio and choose PROFILE: ANALOG STEREO OUTPUT, and secondly, choose PORT: OUTPUT LINE.

Go into the System Settings, and then Multimedia. I'm checking this on 18.04 since my 20.04 machine is elsewhere, so it may be in a different place or called something different on 20.04. Go to the Audio and Video section and look at the Device Preference tab. There you can set the priority of the audio devices available in your system. Put whichever device you want to be the default at the top of the list. Use the "Apply Device List To..." button if you want that default set for everything. Hit Apply. Go to the Audio Hardware Setup tab and set the profile and output settings to whatever it is that you want for the device that you want. Hit Apply. Those are now your defaults.

---

### Post by rafacalifa101 on 2020-07-25
> **CatKiller said:**
> Go into the System Settings, and then Multimedia. I'm checking this on 18.04 since my 20.04 machine is elsewhere, so it may be in a different place or called something different on 20.04. Go to the Audio and Video section and look at the Device Preference tab. There you can set the priority of the audio devices available in your system. Put whichever device you want to be the default at the top of the list. Use the "Apply Device List To..." button if you want that default set for everything. Hit Apply. Go to the Audio Hardware Setup tab and set the profile and output settings to whatever it is that you want for the device that you want. Hit Apply. Those are now your defaults.

Precisely that is what I do, the same as in the video. But it does not remain predetermined. When I log back in, the defaults have changed and I have to start over.

---

### Post by CatKiller on 2020-07-25
> **rafacalifa101 said:**
> Precisely that is what I do, the same as in the video. But it does not remain predetermined. When I log back in, the defaults have changed and I have to start over.

The video is showing using the volume control on the panel. Not the System Settings.

---

### Post by rafacalifa101 on 2020-07-25
> **CatKiller said:**
> The video is showing using the volume control on the panel. Not the System Settings.
Ok. In System Preferences -> Audio Preferences -> Advanced, I have two Internal Audio profiles: Digital Stereo Output (IEC958) and Off. The profile always appears active: Digital Stereo Output (IEC958).

---

### Post by CatKiller on 2020-07-25
You're right. I just checked on my 20.04 laptop and the handy drag-and-drop interface for setting priorities doesn't seem to be there any more. That's a pain.

Edit: I found where they moved it to. If you install **phonon4qt5settings** then you can run **phononsettings** to get the interface that used to be in the System Settings.

---

### Post by rafacalifa101 on 2020-07-25
> **CatKiller said:**
> You're right. I just checked on my 20.04 laptop and the handy drag-and-drop interface for setting priorities doesn't seem to be there any more. That's a pain.

Edit: I found where they moved it to. If you install **phonon4qt5settings** then you can run **phononsettings** to get the interface that used to be in the System Settings.
I have installed that program but it does not allow any solution.

---

