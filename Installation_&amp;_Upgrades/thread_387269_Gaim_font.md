---
title: "Gaim font"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by NooBeee on 2007-03-18
Does anyone know how to change the font of incoming messages?

---

### Post by louis_nichols on 2007-03-18
There is a plugin for gaim, called "gtk theme control", which allows you to customize several font options. I dunno if it will allow changing the font of incoming, as that is set by the sender.

---

### Post by NooBeee on 2007-03-19
couldn't it just override it? trillian can do it......

---

### Post by louis_nichols on 2007-03-19
> **NooBeee said:**
> couldn't it just override it? trillian can do it......

The plugin might be able to do it. I'll give it a try when I get home and get back to you.

---

### Post by louis_nichols on 2007-03-19
OK. It does what you want. You can set the font size for the various areas of the chat window. Please note that not all options are applied immediatelly - some need you to close and reopen the conversation window.

---

### Post by NooBeee on 2007-03-20
Not working for me.  Could you post the contents of your ~/.gaim/gtkrc-2.0    ?  I think the answer is in there.

---

### Post by louis_nichols on 2007-03-20
> **NooBeee said:**
> Not working for me.  Could you post the contents of your ~/.gaim/gtkrc-2.0    ?  I think the answer is in there.

I don't have such a file... I didn't press the button to save the file. What I did, I simply increased the size of all fonts available under the plugin config window, and one of them did the trick, but I dunno which one.

---

### Post by NooBeee on 2007-03-21
the plugin is a gui interface for the config file i think 
it should be in your user account folder under /.gaim/gtkrc-2.0

---

### Post by dank277 on 2007-04-24
I think the extended Prefs plugin contains the functionality that you are seeking.

---

### Post by NooBeee on 2007-04-28
no, none of those plugins worked for me. however i did change the font by changing my gtkrc-2.0 to 

style "imhtml-fix" {
	font-name = "Sans 20"
	font size = "20"
}

---

