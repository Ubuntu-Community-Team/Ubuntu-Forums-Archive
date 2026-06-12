---
title: "Touchpad of laptop does not work during Ubuntu 10.10 installation.."
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by parklinkin on 2011-02-23
Laptop is of the Lenovo 3000 Y500 series, 32bit processor..
Touchpad does not respond during the installation..
Worried if the Touchpad won't work even after the installation..
Currently using Windows7..
Help ! :(

---

### Post by kvarley on 2011-02-23
There is a thread concerning your laptop and the touchpad issue, read it here: [http://ubuntuforums.org/showthread.php?t=1601396]("http://ubuntuforums.org/showthread.php?t=1601396")

Hope this helps! :D Any problems, just post another reply.

---

### Post by parklinkin on 2011-02-23
"Hi

js edit your grub booting option by pressing 'e' at grub screen and add 'i8042.reset' at the end of line where u see 'quite splash'. Press ctrl+x to boot.

Your touchpad will be working and to make that change permanent 
open /etc/default/grub with text editor and add 'i8042.reset' with the line ending with 'quite splash'

save the file close the editor and open a terminal and run 

sudo update-grub

all that worked for me ...my keyboard and touchpad all working fine..tc."


This was the answer I found there.. Will I be able to open the text editor without installing Ubuntu.. ? Or is it that, I should be making the change permanent, only after installing Ubuntu.. ? ?

---

