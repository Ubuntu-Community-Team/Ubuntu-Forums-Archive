---
title: "A balky file won't install"
date: 2016-10-10
forum: Installation &amp; Upgrades
---

### Post by Lloydb39 on 2016-10-10
Since I upgraded to 16.04, everything is working fine except that it keeps trying to install one file and cannot. "ttf-mscorefonts-installer" is the culprit. Doesn't sound like anything critical, but how can I either get it installed or make it quit trying?

---

### Post by howefield on 2016-10-10
What do you mean by "keeps trying to install" - are you getting a popup that looks similar to the attached image ?

---

### Post by Lloydb39 on 2016-10-10
That's the one.

---

### Post by howefield on 2016-10-10
To be honest I use the updated 3.6 ttf-mscorefonts-installer package which unfortunately isn't available in 16.04 but it can be downloaded and installed with apt or gdebi.

Have you got all the fonts actually installed ?

Loading up Libreoffice Writer and looking for andale mono, arial, arial black, comic sans, courier, georgi, impact, times new roman, trebuchet, verdana, and webdings should tell you.

If you actually have the fonts and are lucky the following might get rid of the popup.

```
sudo touch /var/lib/update-notifier/package-data-downloads/ttf-mscorefonts-installer
```

If you haven't got all the fonts but still have the ttf-mscorefonts-installer package in /var/cache/apt/archives/ the following might help..

```
mkdir /home/$USER/mscorefonts && cd /home/$USER/mscorefonts
```
```
grep Url: /usr/share/package-data-downloads/ttf-mscorefonts-installer | awk '{print $2}' | xargs -n 1 wget
```
```
sudo /usr/lib/msttcorefonts/update-ms-fonts /home/$USER/mscorefonts/*
```
```
dpkg-reconfigure ttf-mscorefonts-installer
```

---

### Post by Lloydb39 on 2016-10-11
Excellent answer, complete and understandable. Thanks. I did the sudo touch thing. It didn't show anything in the terminal, so I'll wait to see if the popup returns, and mark this solved if it doesn't.

---

### Post by howefield on 2016-10-11
> **Lloydb39 said:**
> Thanks. I did the sudo touch thing. It didn't show anything in the terminal...

You are welcome, hopefully it will be enough to fix it for you, no output in the terminal is a good thing, generally that means a successful conclusion, (that the command worked, not that the issue is necessarily solved :) ) you'd likely get output in the event of an error.

---

