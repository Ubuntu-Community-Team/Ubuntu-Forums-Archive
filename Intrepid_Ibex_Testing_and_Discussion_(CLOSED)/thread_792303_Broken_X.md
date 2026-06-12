---
title: "Broken X"
date: 2008-05-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by caryb on 2008-05-12
Ok, abit of history, I updated on day 1 & on day 2 my x was broken! So I rebuilt my machine last week back to Hardy as there was no fix for Xorg & there was a missing dep! I just upgraded as I saw this branch opened & bingo I'm back to where I was last week with boken Xorg. Does anyone have a fix for this? I'm running KDE4 Kubuntu but I don't believe it's that as it doesn't get past KDM.


Cheers Cary

---

### Post by seamuso on 2008-05-12
I had kubuntu remix installed and have been grabbing the intrepid updates since the repository appeared a few weeks ago. My x stoppped working during an update last week .. font path errors ..

```
could not init font path element
```

I just reinstalled ubuntu tonight (not remox) so I can see if it was just the kubuntu that caused the problem.

---

### Post by dagrump on 2008-05-12
Repo opening date, #8 might help.

---

### Post by seamuso on 2008-05-12
> **dagrump said:**
> Repo opening date, #8 might help.

that's why I have it running as a vm .. I wanted to see the remix install and I saw the intrepid directory show up a couple of days later. If I didn't expect things to get broken, I wouldn't upgrade .. :)

Anyway, upgraded the new install and downgraded the libxfont to the hardy version and now have x back.

---

### Post by caryb on 2008-05-12
Sorry if I'm thick but what was the outcome is it a Kubuntu error?


Cary

---

### Post by dagrump on 2008-05-12
I'm sorry, I didn't follow the thread, I just noticed issues w/X.

---

### Post by caryb on 2008-05-12
Ok following another post & deciphering the content I have got the temp fix

cd /home/myusername

wget [http://ubuntu.csie.ntu.edu.tw/ubuntu/pool/main/libx/libxfont/libxfont1_1.3.1-2_amd64.deb](http://ubuntu.csie.ntu.edu.tw/ubuntu/pool/main/libx/libxfont/libxfont1_1.3.1-2_amd64.deb)

sudo dpkg -i libxfont1_1.3.1-2_amd64.deb

sudo reboot

This is for 64bit versions only, it will work for Kubuntu & Ubuntu.


Cary

---

### Post by seamuso on 2008-05-12
glad you're fixed

---

### Post by dagrump on 2008-05-12
glad you're fixed, You are a braver human than I!

---

### Post by caryb on 2008-05-15
Solved!:guitar:

---

