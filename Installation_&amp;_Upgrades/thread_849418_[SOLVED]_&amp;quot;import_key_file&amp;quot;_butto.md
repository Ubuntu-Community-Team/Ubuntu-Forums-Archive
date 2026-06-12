---
title: "[SOLVED] &amp;quot;import key file&amp;quot; button crashes 'Software Sources' app"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by rastatech on 2008-07-04
hey Ubuntu folks I'm new to your community after XP-SP3 crashed my AMD64 beyond all hope of redemption, which was the final straw after putting up with windows foibles for 16 years!

I really like Ubuntu so far and you folks have been a fantastic resource - I usually find what I need the answer to just by searching the forums, but this one I couldn't find an answer to, so I'm appealing directly!

I'm trying to install Picasa on Hardy, but when I get to the part of the [instructions]("http://www.google.com/linuxrepositories/ubuntu704.html") that say to import the .pub key file, I press that 'import key file' button and the software sources app or control panel or whatever y'all call it simply closes, as if I'd hit the X in the top right corner. No error, nothing, and it never comes back. I've done this probably 20 times, rebooted, etc. and it just won't do whatever it's supposed to, AFAIK. 

Anyone have a suggestion for me?
TIA!!

---

### Post by Partyboi2 on 2008-07-04
Try another way. Open a terminal (Applications>Accessories>Terminal) and type or paste the commands below.
First download and add the key.
```
sudo wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
apt-get update
```
next adds the repository to your sources.list
```
sudo echo deb http://dl.google.com/linux/deb/ stable non-free | sudo tee -a /etc/apt/sources.list
```
then update
```
sudo apt-get update 
```then to install
```
sudo apt-get install picasa 
```

---

### Post by rastatech on 2008-07-04
This totally worked, awesome, Partyboi2, thank you very much!
It's tricky for us ex-windows/mac people to get used to doing everything command line, but at least using the command line it actually works!

Muchas Gracias! 8)

---

