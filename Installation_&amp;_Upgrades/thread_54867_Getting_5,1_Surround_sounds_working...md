---
title: "Getting 5,1 Surround sounds working.."
date: 2005-08-06
forum: Installation &amp; Upgrades
---

### Post by Matriz on 2005-08-06
I know this has been asked for many times and i have searched forum and still cannot find solution to get 5.1 surround sound working. I have Sound Blaster Live! 5.1 and logitech 5.1 speakers... So what i need is to get Stereo working from Rear speakers too and that 5,1 channel aplications and movies should get working too..iam sorry iam really noob and i just cant find any solution to get 5.1 working. Please Someone,help me on this problem... and i would be again really pleased  ](*,)

---

### Post by Seti on 2005-08-06
With your soundcard your system should be using ALSA (Advanced Linux Sound Architecture) as the driver. So in a console just do```
sudo alsamixer
``` 

you well get a graphics equalizer with which to adjust all your levels. Tab switches between Output, Input and Both. Use the <- and -> keys  switch between master volume. bass, treble etc. There should be two called "Suround". Make sure these are all the way up. (you turn these up with the arrow-up key). One setting is called "Front", you want to turn that one down to about 65-75 so that your front channel doesn't overpower your rear speakers. So adjust stuff in there until the sound is right. I would advise against changing levels of items you are unfamiliar with. Once you're done, hit [ESC]
and then do:```
sudo alsactl store
```

---

### Post by Matriz on 2005-08-06
yes.....but that doesnt work...i dont get stereo sounds from back speakers.... :-?

---

