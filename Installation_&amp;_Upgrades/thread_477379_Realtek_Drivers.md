---
title: "Realtek Drivers"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by Nrad^ on 2007-06-18
Hi, this is my first post so i thought i would make it a constructive one.

I have just recently installed Ubuntu with a dual boot with XP (i want everything to work before i switch completely to Linux) and i must say I love it.

At the moment i have 5.1 surround sound which is connect to my ASUS AN8 SLI deluxe motherboard and i really do not know how to install it.  I think i have to compile the code or something along those lines.  The drivers that i want to download an be found [HERE]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false#2")    I currently have sound on Ubuntu but its i have only one speaker active!

Cheers, Brad

---

### Post by Nrad^ on 2007-06-18
Bump!!!!!:popcorn:

---

### Post by stchman on 2007-06-18
> **Nrad^ said:**
> Hi, this is my first post so i thought i would make it a constructive one.

I have just recently installed Ubuntu with a dual boot with XP (i want everything to work before i switch completely to Linux) and i must say I love it.

At the moment i have 5.1 surround sound which is connect to my ASUS AN8 SLI deluxe motherboard and i really do not know how to install it.  I think i have to compile the code or something along those lines.  The drivers that i want to download an be found [HERE]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false#2")    I currently have sound on Ubuntu but its i have only one speaker active!

Cheers, Brad

Realtek sound cards (AC97) are supported out of the box.  Your mobo has a Realtek ALC850 sound card and there are many that have them working here on the forum.

I have an Audigy 2 and if you double click on the speaker up near the notification area you can add left, right , center and surround volume sliders.

---

### Post by Nrad^ on 2007-06-18
Thanks for the response.

I have done what you have said but i can only see a center option and surround option!  If i click preferences, \I can choose between NVIDIA CK840 (alsa mixer) & Realtek ALC850.  I have tried both and gone through the settings and cannot seem to get either to work:(

---

### Post by Nrad^ on 2007-06-19
I have been researchingon the internet to find a solution to fix my surround problem and I found some resources on how to compile .tar.bz2 files, also i downloaded another driver and it contained a readme telling me how to do the same aswell.  I followed the instructions and this is my result and have no idea why it is doing this! 

```
chmod: cannot access `/dev/amixer1': No such file or directory
mknod: `/dev/amixer2': Permission denied
chown: cannot access `/dev/amixer2': No such file or directory
chmod: cannot access `/dev/amixer2': No such file or directory
mknod: `/dev/amixer3': Permission denied
chown: cannot access `/dev/amixer3': No such file or directory
chmod: cannot access `/dev/amixer3': No such file or directory
done.
rm: cannot remove `/dev/adsp': Permission denied
Creating adsp?...mknod: `/dev/adsp0': Permission denied
chown: cannot access `/dev/adsp0': No such file or directory
chmod: cannot access `/dev/adsp0': No such file or directory
mknod: `/dev/adsp1': Permission denied
chown: cannot access `/dev/adsp1': No such file or directory
chmod: cannot access `/dev/adsp1': No such file or directory
mknod: `/dev/adsp2': Permission denied
chown: cannot access `/dev/adsp2': No such file or directory
chmod: cannot access `/dev/adsp2': No such file or directory
mknod: `/dev/adsp3': Permission denied
chown: cannot access `/dev/adsp3': No such file or directory
chmod: cannot access `/dev/adsp3': No such file or directory
done.
Creating amidi?...mknod: `/dev/amidi0': Permission denied
chown: cannot access `/dev/amidi0': No such file or directory
chmod: cannot access `/dev/amidi0': No such file or directory
mknod: `/dev/amidi1': Permission denied
chown: cannot access `/dev/amidi1': No such file or directory
chmod: cannot access `/dev/amidi1': No such file or directory
mknod: `/dev/amidi2': Permission denied
chown: cannot access `/dev/amidi2': No such file or directory
chmod: cannot access `/dev/amidi2': No such file or directory
mknod: `/dev/amidi3': Permission denied
chown: cannot access `/dev/amidi3': No such file or directory
chmod: cannot access `/dev/amidi3': No such file or directory
done.
Creating admmidi?...mknod: `/dev/admmidi0': Permission denied
chown: cannot access `/dev/admmidi0': No such file or directory
chmod: cannot access `/dev/admmidi0': No such file or directory
mknod: `/dev/admmidi1': Permission denied
chown: cannot access `/dev/admmidi1': No such file or directory
chmod: cannot access `/dev/admmidi1': No such file or directory
mknod: `/dev/admmidi2': Permission denied
chown: cannot access `/dev/admmidi2': No such file or directory
chmod: cannot access `/dev/admmidi2': No such file or directory
mknod: `/dev/admmidi3': Permission denied
chown: cannot access `/dev/admmidi3': No such file or directory
chmod: cannot access `/dev/admmidi3': No such file or directory
done.
ln: cannot remove `/dev/mixer': Permission denied
ln: creating symbolic link `/dev/midi' to `midi00': Permission denied
ln: cannot remove `/dev/dsp': Permission denied
ln: cannot remove `/dev/audio': Permission denied
ln: cannot remove `/dev/sequencer2': Permission denied
ln: cannot remove `/dev/adsp': Permission denied
ln: creating symbolic link `/dev/amidi' to `amidi0': Permission denied
mv: cannot move `/dev/sndstat' to `/dev/1sndstat': Permission denied
rm: cannot remove `/dev/snd': Permission denied
rm: cannot remove `/dev/sndstat': Permission denied
mv: cannot stat `/dev/1sndstat': No such file or directory
rm: cannot remove `/dev/snd/controlC0': Permission denied
rm: cannot remove `/dev/snd/controlC1': Permission denied
rm: cannot remove `/dev/snd/midiC1D0': Permission denied
rm: cannot remove `/dev/snd/pcmC0D0c': Permission denied
rm: cannot remove `/dev/snd/pcmC0D0p': Permission denied
rm: cannot remove `/dev/snd/pcmC0D1c': Permission denied
rm: cannot remove `/dev/snd/pcmC0D2p': Permission denied
rm: cannot remove `/dev/snd/seq': Permission denied
rm: cannot remove `/dev/snd/timer': Permission denied
rmdir: /dev/snd: Permission denied
chown: changing ownership of `/dev/snd': Operation not permitted
chmod: changing permissions of `/dev/snd': Operation not permitted
Creating snd/control?...rm: cannot remove `/dev/snd/controlC0': Permission denied
mknod: `/dev/snd/controlC0': File exists
chown: changing ownership of `/dev/snd/controlC0': Operation not permitted
chmod: changing permissions of `/dev/snd/controlC0': Operation not permitted
rm: cannot remove `/dev/snd/controlC1': Permission denied
mknod: `/dev/snd/controlC1': File exists
chown: changing ownership of `/dev/snd/controlC1': Operation not permitted
chmod: changing permissions of `/dev/snd/controlC1': Operation not permitted
mknod: `/dev/snd/controlC2': Permission denied
chown: cannot access `/dev/snd/controlC2': No such file or directory
chmod: cannot access `/dev/snd/controlC2': No such file or directory
mknod: `/dev/snd/controlC3': Permission denied
chown: cannot access `/dev/snd/controlC3': No such file or directory
chmod: cannot access `/dev/snd/controlC3': No such file or directory
done.
rm: cannot remove `/dev/snd/seq': Permission denied
Creating snd/seq...rm: cannot remove `/dev/snd/seq': Permission denied
mknod: `/dev/snd/seq': File exists
chown: changing ownership of `/dev/snd/seq': Operation not permitted
chmod: changing permissions of `/dev/snd/seq': Operation not permitted
done.
rm: cannot remove `/dev/snd/timer': Permission denied
Creating snd/timer...rm: cannot remove `/dev/snd/timer': Permission denied
mknod: `/dev/snd/timer': File exists
chown: changing ownership of `/dev/snd/timer': Operation not permitted
chmod: changing permissions of `/dev/snd/timer': Operation not permitted
done.
Creating snd/hw??...mknod: `/dev/snd/hwC0D0': Permission denied
chown: cannot access `/dev/snd/hwC0D0': No such file or directory
chmod: cannot access `/dev/snd/hwC0D0': No such file or directory
mknod: `/dev/snd/hwC0D1': Permission denied
chown: cannot access `/dev/snd/hwC0D1': No such file or directory
chmod: cannot access `/dev/snd/hwC0D1': No such file or directory
mknod: `/dev/snd/hwC0D2': Permission denied
chown: cannot access `/dev/snd/hwC0D2': No such file or directory
chmod: cannot access `/dev/snd/hwC0D2': No such file or directory
mknod: `/dev/snd/hwC0D3': Permission denied
chown: cannot access `/dev/snd/hwC0D3': No such file or directory
chmod: cannot access `/dev/snd/hwC0D3': No such file or directory
mknod: `/dev/snd/hwC1D0': Permission denied
chown: cannot access `/dev/snd/hwC1D0': No such file or directory
chmod: cannot access `/dev/snd/hwC1D0': No such file or directory
mknod: `/dev/snd/hwC1D1': Permission denied
chown: cannot access `/dev/snd/hwC1D1': No such file or directory
chmod: cannot access `/dev/snd/hwC1D1': No such file or directory
mknod: `/dev/snd/hwC1D2': Permission denied
chown: cannot access `/dev/snd/hwC1D2': No such file or directory
chmod: cannot access `/dev/snd/hwC1D2': No such file or directory
mknod: `/dev/snd/hwC1D3': Permission denied
chown: cannot access `/dev/snd/hwC1D3': No such file or directory
chmod: cannot access `/dev/snd/hwC1D3': No such file or directory
mknod: `/dev/snd/hwC2D0': Permission denied
chown: cannot access `/dev/snd/hwC2D0': No such file or directory
chmod: cannot access `/dev/snd/hwC2D0': No such file or directory
mknod: `/dev/snd/hwC2D1': Permission denied
chown: cannot access `/dev/snd/hwC2D1': No such file or directory
chmod: cannot access `/dev/snd/hwC2D1': No such file or directory
mknod: `/dev/snd/hwC2D2': Permission denied
chown: cannot access `/dev/snd/hwC2D2': No such file or directory
chmod: cannot access `/dev/snd/hwC2D2': No such file or directory
mknod: `/dev/snd/hwC2D3': Permission denied
chown: cannot access `/dev/snd/hwC2D3': No such file or directory
chmod: cannot access `/dev/snd/hwC2D3': No such file or directory
mknod: `/dev/snd/hwC3D0': Permission denied
chown: cannot access `/dev/snd/hwC3D0': No such file or directory
chmod: cannot access `/dev/snd/hwC3D0': No such file or directory
mknod: `/dev/snd/hwC3D1': Permission denied
chown: cannot access `/dev/snd/hwC3D1': No such file or directory
chmod: cannot access `/dev/snd/hwC3D1': No such file or directory
mknod: `/dev/snd/hwC3D2': Permission denied
chown: cannot access `/dev/snd/hwC3D2': No such file or directory
chmod: cannot access `/dev/snd/hwC3D2': No such file or directory
mknod: `/dev/snd/hwC3D3': Permission denied
chown: cannot access `/dev/snd/hwC3D3': No such file or directory
chmod: cannot access `/dev/snd/hwC3D3': No such file or directory
done.
Creating snd/midi??...mknod: `/dev/snd/midiC0D0': Permission denied
chown: cannot access `/dev/snd/midiC0D0': No such file or directory
chmod: cannot access `/dev/snd/midiC0D0': No such file or directory
mknod: `/dev/snd/midiC0D1': Permission denied
chown: cannot access `/dev/snd/midiC0D1': No such file or directory
chmod: cannot access `/dev/snd/midiC0D1': No such file or directory
mknod: `/dev/snd/midiC0D2': Permission denied
chown: cannot access `/dev/snd/midiC0D2': No such file or directory
chmod: cannot access `/dev/snd/midiC0D2': No such file or directory
mknod: `/dev/snd/midiC0D3': Permission denied
chown: cannot access `/dev/snd/midiC0D3': No such file or directory
chmod: cannot access `/dev/snd/midiC0D3': No such file or directory
mknod: `/dev/snd/midiC0D4': Permission denied
chown: cannot access `/dev/snd/midiC0D4': No such file or directory
chmod: cannot access `/dev/snd/midiC0D4': No such file or directory
mknod: `/dev/snd/midiC0D5': Permission denied
chown: cannot access `/dev/snd/midiC0D5': No such file or directory
chmod: cannot access `/dev/snd/midiC0D5': No such file or directory
mknod: `/dev/snd/midiC0D6': Permission denied
chown: cannot access `/dev/snd/midiC0D6': No such file or directory
chmod: cannot access `/dev/snd/midiC0D6': No such file or directory
mknod: `/dev/snd/midiC0D7': Permission denied
chown: cannot access `/dev/snd/midiC0D7': No such file or directory
chmod: cannot access `/dev/snd/midiC0D7': No such file or directory
rm: cannot remove `/dev/snd/midiC1D0': Permission denied
mknod: `/dev/snd/midiC1D0': File exists
chown: changing ownership of `/dev/snd/midiC1D0': Operation not permitted
chmod: changing permissions of `/dev/snd/midiC1D0': Operation not permitted
mknod: `/dev/snd/midiC1D1': Permission denied
chown: cannot access `/dev/snd/midiC1D1': No such file or directory
chmod: cannot access `/dev/snd/midiC1D1': No such file or directory
mknod: `/dev/snd/midiC1D2': Permission denied
chown: cannot access `/dev/snd/midiC1D2': No such file or directory
chmod: cannot access `/dev/snd/midiC1D2': No such file or directory
mknod: `/dev/snd/midiC1D3': Permission denied
chown: cannot access `/dev/snd/midiC1D3': No such file or directory
chmod: cannot access `/dev/snd/midiC1D3': No such file or directory
mknod: `/dev/snd/midiC1D4': Permission denied
chown: cannot access `/dev/snd/midiC1D4': No such file or directory
chmod: cannot access `/dev/snd/midiC1D4': No such file or directory
mknod: `/dev/snd/midiC1D5': Permission denied
chown: cannot access `/dev/snd/midiC1D5': No such file or directory
chmod: cannot access `/dev/snd/midiC1D5': No such file or directory
mknod: `/dev/snd/midiC1D6': Permission denied
chown: cannot access `/dev/snd/midiC1D6': No such file or directory
chmod: cannot access `/dev/snd/midiC1D6': No such file or directory
mknod: `/dev/snd/midiC1D7': Permission denied
chown: cannot access `/dev/snd/midiC1D7': No such file or directory
chmod: cannot access `/dev/snd/midiC1D7': No such file or directory
mknod: `/dev/snd/midiC2D0': Permission denied
chown: cannot access `/dev/snd/midiC2D0': No such file or directory
chmod: cannot access `/dev/snd/midiC2D0': No such file or directory
mknod: `/dev/snd/midiC2D1': Permission denied
chown: cannot access `/dev/snd/midiC2D1': No such file or directory
chmod: cannot access `/dev/snd/midiC2D1': No such file or directory
mknod: `/dev/snd/midiC2D2': Permission denied
chown: cannot access `/dev/snd/midiC2D2': No such file or directory
chmod: cannot access `/dev/snd/midiC2D2': No such file or directory
mknod: `/dev/snd/midiC2D3': Permission denied
chown: cannot access `/dev/snd/midiC2D3': No such file or directory
chmod: cannot access `/dev/snd/midiC2D3': No such file or directory
mknod: `/dev/snd/midiC2D4': Permission denied
chown: cannot access `/dev/snd/midiC2D4': No such file or directory
chmod: cannot access `/dev/snd/midiC2D4': No such file or directory
mknod: `/dev/snd/midiC2D5': Permission denied
chown: cannot access `/dev/snd/midiC2D5': No such file or directory
chmod: cannot access `/dev/snd/midiC2D5': No such file or directory
mknod: `/dev/snd/midiC2D6': Permission denied
chown: cannot access `/dev/snd/midiC2D6': No such file or directory
chmod: cannot access `/dev/snd/midiC2D6': No such file or directory
mknod: `/dev/snd/midiC2D7': Permission denied
chown: cannot access `/dev/snd/midiC2D7': No such file or directory
chmod: cannot access `/dev/snd/midiC2D7': No such file or directory
mknod: `/dev/snd/midiC3D0': Permission denied
chown: cannot access `/dev/snd/midiC3D0': No such file or directory
chmod: cannot access `/dev/snd/midiC3D0': No such file or directory
mknod: `/dev/snd/midiC3D1': Permission denied
chown: cannot access `/dev/snd/midiC3D1': No such file or directory
chmod: cannot access `/dev/snd/midiC3D1': No such file or directory
mknod: `/dev/snd/midiC3D2': Permission denied
chown: cannot access `/dev/snd/midiC3D2': No such file or directory
chmod: cannot access `/dev/snd/midiC3D2': No such file or directory
mknod: `/dev/snd/midiC3D3': Permission denied
chown: cannot access `/dev/snd/midiC3D3': No such file or directory
chmod: cannot access `/dev/snd/midiC3D3': No such file or directory
mknod: `/dev/snd/midiC3D4': Permission denied
chown: cannot access `/dev/snd/midiC3D4': No such file or directory
chmod: cannot access `/dev/snd/midiC3D4': No such file or directory
mknod: `/dev/snd/midiC3D5': Permission denied
chown: cannot access `/dev/snd/midiC3D5': No such file or directory
chmod: cannot access `/dev/snd/midiC3D5': No such file or directory
mknod: `/dev/snd/midiC3D6': Permission denied
chown: cannot access `/dev/snd/midiC3D6': No such file or directory
chmod: cannot access `/dev/snd/midiC3D6': No such file or directory
mknod: `/dev/snd/midiC3D7': Permission denied
chown: cannot access `/dev/snd/midiC3D7': No such file or directory
chmod: cannot access `/dev/snd/midiC3D7': No such file or directory
done.
Creating snd/pcm??p...rm: cannot remove `/dev/snd/pcmC0D0p': Permission denied
mknod: `/dev/snd/pcmC0D0p': File exists
chown: changing ownership of `/dev/snd/pcmC0D0p': Operation not permitted
chmod: changing permissions of `/dev/snd/pcmC0D0p': Operation not permitted
mknod: `/dev/snd/pcmC0D1p': Permission denied
chown: cannot access `/dev/snd/pcmC0D1p': No such file or directory
chmod: cannot access `/dev/snd/pcmC0D1p': No such file or directory
rm: cannot remove `/dev/snd/pcmC0D2p': Permission denied
mknod: `/dev/snd/pcmC0D2p': File exists
chown: changing ownership of `/dev/snd/pcmC0D2p': Operation not permitted
chmod: changing permissions of `/dev/snd/pcmC0D2p': Operation not permitted
mknod: `/dev/snd/pcmC0D3p': Permission denied
chown: cannot access `/dev/snd/pcmC0D3p': No such file or directory
chmod: cannot access `/dev/snd/pcmC0D3p': No such file or directory
mknod: `/dev/snd/pcmC0D4p': Permission denied
chown: cannot access `/dev/snd/pcmC0D4p': No such file or directory
chmod: cannot access `/dev/snd/pcmC0D4p': No such file or directory
mknod: `/dev/snd/pcmC0D5p': Permission denied
chown: cannot access `/dev/snd/pcmC0D5p': No such file or directory
chmod: cannot access `/dev/snd/pcmC0D5p': No such file or directory
mknod: `/dev/snd/pcmC0D6p': Permission denied
chown: cannot access `/dev/snd/pcmC0D6p': No such file or directory
chmod: cannot access `/dev/snd/pcmC0D6p': No such file or directory
mknod: `/dev/snd/pcmC0D7p': Permission denied
chown: cannot access `/dev/snd/pcmC0D7p': No such file or directory
chmod: cannot access `/dev/snd/pcmC0D7p': No such file or directory
mknod: `/dev/snd/pcmC1D0p': Permission denied
chown: cannot access `/dev/snd/pcmC1D0p': No such file or directory
chmod: cannot access `/dev/snd/pcmC1D0p': No such file or directory
mknod: `/dev/snd/pcmC1D1p': Permission denied
chown: cannot access `/dev/snd/pcmC1D1p': No such file or directory
chmod: cannot access `/dev/snd/pcmC1D1p': No such file or directory
mknod: `/dev/snd/pcmC1D2p': Permission denied
chown: cannot access `/dev/snd/pcmC1D2p': No such file or directory
chmod: cannot access `/dev/snd/pcmC1D2p': No such file or directory
mknod: `/dev/snd/pcmC1D3p': Permission denied
chown: cannot access `/dev/snd/pcmC1D3p': No such file or directory
chmod: cannot access `/dev/snd/pcmC1D3p': No such file or directory
mknod: `/dev/snd/pcmC1D4p': Permission denied
chown: cannot access `/dev/snd/pcmC1D4p': No such file or directory
chmod: cannot access `/dev/snd/pcmC1D4p': No such file or directory
mknod: `/dev/snd/pcmC1D5p': Permission denied
chown: cannot access `/dev/snd/pcmC1D5p': No such file or directory
chmod: cannot access `/dev/snd/pcmC1D5p': No such file or directory
mknod: `/dev/snd/pcmC1D6p': Permission denied
chown: cannot access `/dev/snd/pcmC1D6p': No such file or directory
chmod: cannot access `/dev/snd/pcmC1D6p': No such file or directory
mknod: `/dev/snd/pcmC1D7p': Permission denied
chown: cannot access `/dev/snd/pcmC1D7p': No such file or directory
chmod: cannot access `/dev/snd/pcmC1D7p': No such file or directory
mknod: `/dev/snd/pcmC2D0p': Permission denied
chown: cannot access `/dev/snd/pcmC2D0p': No such file or directory
chmod: cannot access `/dev/snd/pcmC2D0p': No such file or directory
mknod: `/dev/snd/pcmC2D1p': Permission denied
chown: cannot access `/dev/snd/pcmC2D1p': No such file or directory
chmod: cannot access `/dev/snd/pcmC2D1p': No such file or directory
mknod: `/dev/snd/pcmC2D2p': Permission denied
chown: cannot access `/dev/snd/pcmC2D2p': No such file or directory
chmod: cannot access `/dev/snd/pcmC2D2p': No such file or directory
mknod: `/dev/snd/pcmC2D3p': Permission denied
chown: cannot access `/dev/snd/pcmC2D3p': No such file or directory
chmod: cannot access `/dev/snd/pcmC2D3p': No such file or directory
mknod: `/dev/snd/pcmC2D4p': Permission denied
chown: cannot access `/dev/snd/pcmC2D4p': No such file or directory
chmod: cannot access `/dev/snd/pcmC2D4p': No such file or directory
mknod: `/dev/snd/pcmC2D5p': Permission denied
chown: cannot access `/dev/snd/pcmC2D5p': No such file or directory
chmod: cannot access `/dev/snd/pcmC2D5p': No such file or directory
mknod: `/dev/snd/pcmC2D6p': Permission denied
chown: cannot access `/dev/snd/pcmC2D6p': No such file or directory
chmod: cannot access `/dev/snd/pcmC2D6p': No such file or directory
mknod: `/dev/snd/pcmC2D7p': Permission denied
chown: cannot access `/dev/snd/pcmC2D7p': No such file or directory
chmod: cannot access `/dev/snd/pcmC2D7p': No such file or directory
mknod: `/dev/snd/pcmC3D0p': Permission denied
chown: cannot access `/dev/snd/pcmC3D0p': No such file or directory
chmod: cannot access `/dev/snd/pcmC3D0p': No such file or directory
mknod: `/dev/snd/pcmC3D1p': Permission denied
chown: cannot access `/dev/snd/pcmC3D1p': No such file or directory
chmod: cannot access `/dev/snd/pcmC3D1p': No such file or directory
mknod: `/dev/snd/pcmC3D2p': Permission denied
chown: cannot access `/dev/snd/pcmC3D2p': No such file or directory
chmod: cannot access `/dev/snd/pcmC3D2p': No such file or directory
mknod: `/dev/snd/pcmC3D3p': Permission denied
chown: cannot access `/dev/snd/pcmC3D3p': No such file or directory
chmod: cannot access `/dev/snd/pcmC3D3p': No such file or directory
mknod: `/dev/snd/pcmC3D4p': Permission denied
chown: cannot access `/dev/snd/pcmC3D4p': No such file or directory
chmod: cannot access `/dev/snd/pcmC3D4p': No such file or directory
mknod: `/dev/snd/pcmC3D5p': Permission denied
chown: cannot access `/dev/snd/pcmC3D5p': No such file or directory
chmod: cannot access `/dev/snd/pcmC3D5p': No such file or directory
mknod: `/dev/snd/pcmC3D6p': Permission denied
chown: cannot access `/dev/snd/pcmC3D6p': No such file or directory
chmod: cannot access `/dev/snd/pcmC3D6p': No such file or directory
mknod: `/dev/snd/pcmC3D7p': Permission denied
chown: cannot access `/dev/snd/pcmC3D7p': No such file or directory
chmod: cannot access `/dev/snd/pcmC3D7p': No such file or directory
done.
Creating snd/pcm??c...rm: cannot remove `/dev/snd/pcmC0D0c': Permission denied
mknod: `/dev/snd/pcmC0D0c': File exists
chown: changing ownership of `/dev/snd/pcmC0D0c': Operation not permitted
chmod: changing permissions of `/dev/snd/pcmC0D0c': Operation not permitted
rm: cannot remove `/dev/snd/pcmC0D1c': Permission denied
mknod: `/dev/snd/pcmC0D1c': File exists
chown: changing ownership of `/dev/snd/pcmC0D1c': Operation not permitted
chmod: changing permissions of `/dev/snd/pcmC0D1c': Operation not permitted
mknod: `/dev/snd/pcmC0D2c': Permission denied
chown: cannot access `/dev/snd/pcmC0D2c': No such file or directory
chmod: cannot access `/dev/snd/pcmC0D2c': No such file or directory
mknod: `/dev/snd/pcmC0D3c': Permission denied
chown: cannot access `/dev/snd/pcmC0D3c': No such file or directory
chmod: cannot access `/dev/snd/pcmC0D3c': No such file or directory
mknod: `/dev/snd/pcmC0D4c': Permission denied
chown: cannot access `/dev/snd/pcmC0D4c': No such file or directory
chmod: cannot access `/dev/snd/pcmC0D4c': No such file or directory
mknod: `/dev/snd/pcmC0D5c': Permission denied
chown: cannot access `/dev/snd/pcmC0D5c': No such file or directory
chmod: cannot access `/dev/snd/pcmC0D5c': No such file or directory
mknod: `/dev/snd/pcmC0D6c': Permission denied
chown: cannot access `/dev/snd/pcmC0D6c': No such file or directory
chmod: cannot access `/dev/snd/pcmC0D6c': No such file or directory
mknod: `/dev/snd/pcmC0D7c': Permission denied
chown: cannot access `/dev/snd/pcmC0D7c': No such file or directory
chmod: cannot access `/dev/snd/pcmC0D7c': No such file or directory
mknod: `/dev/snd/pcmC1D0c': Permission denied
chown: cannot access `/dev/snd/pcmC1D0c': No such file or directory
chmod: cannot access `/dev/snd/pcmC1D0c': No such file or directory
mknod: `/dev/snd/pcmC1D1c': Permission denied
chown: cannot access `/dev/snd/pcmC1D1c': No such file or directory
chmod: cannot access `/dev/snd/pcmC1D1c': No such file or directory
mknod: `/dev/snd/pcmC1D2c': Permission denied
chown: cannot access `/dev/snd/pcmC1D2c': No such file or directory
chmod: cannot access `/dev/snd/pcmC1D2c': No such file or directory
mknod: `/dev/snd/pcmC1D3c': Permission denied
chown: cannot access `/dev/snd/pcmC1D3c': No such file or directory
chmod: cannot access `/dev/snd/pcmC1D3c': No such file or directory
mknod: `/dev/snd/pcmC1D4c': Permission denied
chown: cannot access `/dev/snd/pcmC1D4c': No such file or directory
chmod: cannot access `/dev/snd/pcmC1D4c': No such file or directory
mknod: `/dev/snd/pcmC1D5c': Permission denied
chown: cannot access `/dev/snd/pcmC1D5c': No such file or directory
chmod: cannot access `/dev/snd/pcmC1D5c': No such file or directory
mknod: `/dev/snd/pcmC1D6c': Permission denied
chown: cannot access `/dev/snd/pcmC1D6c': No such file or directory
chmod: cannot access `/dev/snd/pcmC1D6c': No such file or directory
mknod: `/dev/snd/pcmC1D7c': Permission denied
chown: cannot access `/dev/snd/pcmC1D7c': No such file or directory
chmod: cannot access `/dev/snd/pcmC1D7c': No such file or directory
mknod: `/dev/snd/pcmC2D0c': Permission denied
chown: cannot access `/dev/snd/pcmC2D0c': No such file or directory
chmod: cannot access `/dev/snd/pcmC2D0c': No such file or directory
mknod: `/dev/snd/pcmC2D1c': Permission denied
chown: cannot access `/dev/snd/pcmC2D1c': No such file or directory
chmod: cannot access `/dev/snd/pcmC2D1c': No such file or directory
mknod: `/dev/snd/pcmC2D2c': Permission denied
chown: cannot access `/dev/snd/pcmC2D2c': No such file or directory
chmod: cannot access `/dev/snd/pcmC2D2c': No such file or directory
mknod: `/dev/snd/pcmC2D3c': Permission denied
chown: cannot access `/dev/snd/pcmC2D3c': No such file or directory
chmod: cannot access `/dev/snd/pcmC2D3c': No such file or directory
mknod: `/dev/snd/pcmC2D4c': Permission denied
chown: cannot access `/dev/snd/pcmC2D4c': No such file or directory
chmod: cannot access `/dev/snd/pcmC2D4c': No such file or directory
mknod: `/dev/snd/pcmC2D5c': Permission denied
chown: cannot access `/dev/snd/pcmC2D5c': No such file or directory
chmod: cannot access `/dev/snd/pcmC2D5c': No such file or directory
mknod: `/dev/snd/pcmC2D6c': Permission denied
chown: cannot access `/dev/snd/pcmC2D6c': No such file or directory
chmod: cannot access `/dev/snd/pcmC2D6c': No such file or directory
mknod: `/dev/snd/pcmC2D7c': Permission denied
chown: cannot access `/dev/snd/pcmC2D7c': No such file or directory
chmod: cannot access `/dev/snd/pcmC2D7c': No such file or directory
mknod: `/dev/snd/pcmC3D0c': Permission denied
chown: cannot access `/dev/snd/pcmC3D0c': No such file or directory
chmod: cannot access `/dev/snd/pcmC3D0c': No such file or directory
mknod: `/dev/snd/pcmC3D1c': Permission denied
chown: cannot access `/dev/snd/pcmC3D1c': No such file or directory
chmod: cannot access `/dev/snd/pcmC3D1c': No such file or directory
mknod: `/dev/snd/pcmC3D2c': Permission denied
chown: cannot access `/dev/snd/pcmC3D2c': No such file or directory
chmod: cannot access `/dev/snd/pcmC3D2c': No such file or directory
mknod: `/dev/snd/pcmC3D3c': Permission denied
chown: cannot access `/dev/snd/pcmC3D3c': No such file or directory
chmod: cannot access `/dev/snd/pcmC3D3c': No such file or directory
mknod: `/dev/snd/pcmC3D4c': Permission denied
chown: cannot access `/dev/snd/pcmC3D4c': No such file or directory
chmod: cannot access `/dev/snd/pcmC3D4c': No such file or directory
mknod: `/dev/snd/pcmC3D5c': Permission denied
chown: cannot access `/dev/snd/pcmC3D5c': No such file or directory
chmod: cannot access `/dev/snd/pcmC3D5c': No such file or directory
mknod: `/dev/snd/pcmC3D6c': Permission denied
chown: cannot access `/dev/snd/pcmC3D6c': No such file or directory
chmod: cannot access `/dev/snd/pcmC3D6c': No such file or directory
mknod: `/dev/snd/pcmC3D7c': Permission denied
chown: cannot access `/dev/snd/pcmC3D7c': No such file or directory
chmod: cannot access `/dev/snd/pcmC3D7c': No such file or directory
done.
Creating aload?...mknod: `/dev/aloadC0': Permission denied
chown: cannot access `/dev/aloadC0': No such file or directory
chmod: cannot access `/dev/aloadC0': No such file or directory
mknod: `/dev/aloadC1': Permission denied
chown: cannot access `/dev/aloadC1': No such file or directory
chmod: cannot access `/dev/aloadC1': No such file or directory
mknod: `/dev/aloadC2': Permission denied
chown: cannot access `/dev/aloadC2': No such file or directory
chmod: cannot access `/dev/aloadC2': No such file or directory
mknod: `/dev/aloadC3': Permission denied
chown: cannot access `/dev/aloadC3': No such file or directory
chmod: cannot access `/dev/aloadC3': No such file or directory
done.
Creating aloadSEQ...mknod: `/dev/aloadSEQ': Permission denied
chown: cannot access `/dev/aloadSEQ': No such file or directory
chmod: cannot access `/dev/aloadSEQ': No such file or directory
done.
Remove old alsa library
Compile ALSA Library.....
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** No targets specified and no makefile found. Stop.
make: *** No rule to make target `install'. Stop.
Compile ALSA Utility......
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** No targets specified and no makefile found. Stop.
make: *** No rule to make target `install'. Stop.
ln: creating symbolic link `/dev/sndstat' to `/proc/asound/oss/sndstat': File exists
cp: cannot create regular file `/usr/share/sounds/alsa/test.wav': Permission denied
Remove Folder.....
./install: 102: alsaconf: not found
brad@Brad-PC:~/Desktop/realtek-linux-audiopack-4.06a$ 


```

---

### Post by bdig on 2007-06-19
I have the same motherboard, and my card was also not recognised.
I have a PCI soundcard that I use primarily, but wanted to get the onboard sound working as well, so that I'd have two soundcards in order to try out some DJ software.
If anyone has managed to solve this problem in the past, I'd love to hear how.

Thanks.

---

### Post by Nrad^ on 2007-06-20
Bump!:popcorn::p

---

