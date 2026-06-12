---
title: "Frostwire/Limewire Install Problems"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by Sophistasista on 2008-06-12
Hi there

So I'm trying to install either Limewire or Frostwire (which I've not heard of before).

I originally tried installing Limewire. It hung in on installing "sun-java6-bin", so I tried re-starting. Then when I went to download again it kept saying I had to close the other installer .. there was nothing else open. I followed advice on other forum posts, and doing "sudo dpkg --configure -a" seemed to fix it. But then it hung again. 

So I gave up on Limewire, and discovered Frostwire. 

Unfortunately I didn't get very far. It said there was a broken cache. Again, following various suggestions on different forum posts, I'm now trying to install sun-java6-bin through Terminal. Except I now get the below which is also hanging;

[Screenshot]("http://http://i38.photobucket.com/albums/e109/Sophistasista/Screenshot.png")

So now I'm at a complete loss!

Please can someone give me some pointers? Also please bear in mind I have only just switched to Ubuntu from Windows.

---

### Post by Vivaldi Gloria on 2008-06-12
There is a problem with your screenshot link. Here is the correct one:

[http://i38.photobucket.com/albums/e109/Sophistasista/Screenshot.png](http://i38.photobucket.com/albums/e109/Sophistasista/Screenshot.png)

---

### Post by Vivaldi Gloria on 2008-06-12
Have you tried clicking tab key then enter or space?

You can also try

sudo apt-get install -y sun-java6-bin

Here -y means answer yes to everything automatically.

---

