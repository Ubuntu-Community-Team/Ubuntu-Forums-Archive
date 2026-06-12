---
title: "Gutsy splash screen background color"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by punkybouy on 2008-02-02
I updated to Gutsy but my blue splash screen color is now back to brown.  I have looked at all the GUI options and they point to blue.  I had this issue on a new install on a laptop a few weeks ago and had to edit a file manually and change a color code.  Anyone have any ideas?  Thanks.
Don't confuse the login screen color with the splash screen color.  I know splash screens are not installed in Gutsy by default but I have one and like it.

---

### Post by punkybouy on 2008-02-02
Hmm, I am getting good at answering my own questions.  In this case you have to edit the file /etc/gdm/PreSession/Default and find the line "default value' and there you will see a code with the value "dab082".  Change that to the code of your choice.
You can go to System\Preferences\Login Window and go to the local tab.  In there you will see an entry called "background color"  click there and any color you choose will have a hex code listed to the right.  Use the number for the color of your choice.
I think this solution is here in the forum somewhere but I found it doing a web search.

---

### Post by ilovenicotine on 2008-02-02
> **punkybouy said:**
> Hmm, I am getting good at answering my own questions.  In this case you have to edit the file /etc/gdm/PreSession/Default and find the line "default value' and there you will see a code with the value "dab082".  Change that to the code of your choice.
You can go to System\Preferences\Login Window and go to the local tab.  In there you will see an entry called "background color"  click there and any color you choose will have a hex code listed to the right.  Use the number for the color of your choice.
I think this solution is here in the forum somewhere but I found it doing a web search.


Works perfectly in Gutsy, Thanks!

---

### Post by delsvr on 2008-02-02
Yup. Nice find. Good job. Thanks.

---

