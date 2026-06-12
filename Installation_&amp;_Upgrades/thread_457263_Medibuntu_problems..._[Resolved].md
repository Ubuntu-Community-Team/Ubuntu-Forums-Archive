---
title: "Medibuntu problems... [Resolved]"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by Znupi on 2007-05-28
I wanted to install google earth, so I checked this: [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth) which lead me to [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) . I have enabled Medibuntu repositories, of course, by running:
```

wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O - | sudo apt-key add -
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
sudo sed -e 's/ non-free//' -i /etc/apt/sources.list.d/medibuntu.list

```
And, I can't find Google Earth in Synaptic, and the strange thing is, I've run
```

cat /etc/apt/sources.list | grep medibuntu

```
And there was no output. But I know medibuntu has been enabled, because there are new applications in **Add/Remove...** and because if I go to **System -> Administration -> Software Sources** I can see medibuntu repos.

What now?

---

### Post by Znupi on 2007-05-28
Nevermind, I got it, I shouldn't have run the last command. Also, Google Earth doesn't show up in **Add/Remove...** but it does in **Synaptic**.

---

