---
title: "installing software off repository after copying all files from the repository disc."
date: 2012-07-08
forum: Installation &amp; Upgrades
---

### Post by moderndayeskimo on 2012-07-08
im having trouble installin dvd libraries and other system sensitive files. i ordered the 64 bit install/live cd along with the whole repository on dvd's. after goin through each disc and copying them im having trouble installing the required libraries to watch dvd's as well as other installations from the repository. ive tried runnin the scripts in the terminal but i get a message saying that they have already been installed and require no further actions. id really like to get my ubuntu system ready and goin. thank you for your time and patience helping me out.

---

### Post by oldos2er on 2012-07-08
To watch commercial DVDs you need to install libdvdcss2, from the Medibuntu repository. See [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by moderndayeskimo on 2012-07-08
after runnin the script the page you linked gave me the terminal is saying the library is already installed and in use. but when i open up the default video player and vlc they come up with the error saying i do not have the ability to play back encrypted dvds. what do i do now?

---

### Post by oldos2er on 2012-07-08
Odd. Can you run this command and post the output here? ```
apt-cache policy libdvdcss2
```

---

