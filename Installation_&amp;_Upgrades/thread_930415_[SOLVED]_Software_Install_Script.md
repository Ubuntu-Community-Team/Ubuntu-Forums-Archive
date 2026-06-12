---
title: "[SOLVED] Software Install Script"
date: 2008-09-26
forum: Installation &amp; Upgrades
---

### Post by smirnoff76 on 2008-09-26
Hi Everyone 

I am wanting to create a script to automate the install of various pieces of software, the script I have in mind would be something as follows:

sudo apt-get install vlc compiz wormux wormux-data

okay maybe not these specific packages but you get the idea. 
I have two questions would the format of the command put together there work? If not does anyone have an example they could show? Also when putting the file together what extension should the file be saved as? Would I need to make the file executable? 

Any help would be really appreciated so thanks in advance!!

---

### Post by Partyboi2 on 2008-09-26
Open a text editor and do something like
```
#!/bin/bash
apt-get install vlc compiz wormux wormux-data
```
Save the file as whatever.sh
Then in a terminal make it excutable
```
 chmod +x whatever.sh
```
then run the script by
```
sudo ./whatever.sh
```
* change whatever to what you want.

---

### Post by smirnoff76 on 2008-09-26
Great thanks for that partyboi2. 

Going in the other direction, if i was to put a script together for doing a complete removal of various software app's then presumaby the script would be something like this then:

sudo apt-get remove packageA packageB
sudo apt-get clean

Assuming the second line is correct would it actually need sudo specifying again? And am I also right in thinking that by running clean that would also remove any associated config files relating to package A and B?

---

