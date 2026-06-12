---
title: "Re-Install, Format, Fix? What shall I do and how?"
date: 2005-12-03
forum: Installation &amp; Upgrades
---

### Post by Cuppa-Chino on 2005-12-03
Hi,

I actually had my Ubuntu working rather well... until I tried installing my webcam that is. Since then it has gone totally AWOL I cannot get into the Internet anymore, cannot get my Wireless card (ndiswrapper w/ wg311v2.inf  & wpa_supplicant) to work at all

I have tried 
[LIST]
[*]re-installing my wireless card both by reinstalling just ndiswrapper / wpa_supplicant and by doing both in one go
[*]reinstalling kernel 2.6.12.10-686smp
[*]have re-checked all my conf files again and again
[/LIST]

I am really at a loss, I would be happy to forefeit the webcam just to get back to where I was (for a while at least) but how can I do a "reinstall" without formatting, what other options do I have?

I spent hours and several formats to get the system up in the first place, I am totally frustrated and the thought of having to everything again and potentially loose a whole lot of stuff is very demoralising :cry: please give me a pointer

---

### Post by mo_x on 2005-12-03
What did you do to install you webcam?

---

### Post by Cuppa-Chino on 2005-12-03
I just followed the instructions in this thread:

[HOWTO: Making ICM532 chipset based webcams work on breezy]("http://ubuntuforums.org/showthread.php?t=75284")
you might see a question of mine on that thread, I waited for arnieboy's answer before following his instructions exactly...

since then I have re-installed kernel & headers -- so webcam now no longer works !

---

### Post by bwog on 2005-12-03
For future reference, this thread contains some info on making backups: [http://ubuntuforums.org/showthread.php?t=59148&highlight=home+backup](http://ubuntuforums.org/showthread.php?t=59148&highlight=home+backup)

I understand that when you have a separate home directory, your files wont be lost when you have to reinstall. However, I have never done this myself, so try to figure out if there are any precautions necessary.

You can also read and  backup your ubuntu files from windows with explore2fs.

---

### Post by Cuppa-Chino on 2005-12-03
thanks will keep the backup in mind, but is there no way I can get around an all out install?

maybe by uninstalling ndiswrapper, wpa_supplicant & 686smp kernel and than reinstalling all that?

---

### Post by bwog on 2005-12-03
Maybe there is a way around reinstalling. You can wait if someone has a better answer.

However, what you are suggesting takes as much time as reinstalling. Installing will be easier the second time. Still, not a nice decision to make. Good luck.

I just thought it would be nice to know that with system backup youwont have to do this a third or fourth time.

---

### Post by manicka on 2005-12-03
[QUOTE=Cuppa-Chino]thanks will keep the backup in mind, but is there no way I can get around an all out install?

maybe by uninstalling ndiswrapper, wpa_supplicant & 686smp kernel and than reinstalling all that?[/QUOTE]

Do you still have your old kernel installed?. Boot into that and see if some of your problems are solved.

---

### Post by Cuppa-Chino on 2005-12-14
it was format & format again that brought me back to a semi-stable ubuntu...

---

