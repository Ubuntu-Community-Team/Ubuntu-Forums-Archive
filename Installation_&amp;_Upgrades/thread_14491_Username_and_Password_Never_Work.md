---
title: "Username and Password Never Work?"
date: 2005-02-07
forum: Installation &amp; Upgrades
---

### Post by blindgoat on 2005-02-07
I just recently installed Ubuntu hoary-install-i386.iso array-1. At the point where it asks for hostname I type blindgoat - it asks for username I type blindgoat - it asks for password - I type my password, then confirm it. It goes to the login page, I type in blindgoat and my pswd and it always says something like "Incorrect uesrname and password". I reinstalled it, made CERTAIN that I had the EXACT username and passoword that I wanted and then tried logging in again. WHAT is going on? It seems like when I type in my username and password to register them, it looks like there's an extra space at the beginning but I didn't type it. I know this is retarded and I'm not this big of a noob but I don't want to reinstall again and have the same problem. If anyone has had this problem and knows wtf I am doing wrong please help me. Is there some way I can recover my pswd and username? or set a new one? OR SOMETHING?

I just reinstalled one more time and took pictures of the 3 screens. You can see them here: [http://blindgoat.net/other](http://blindgoat.net/other) - Please someone help - my friend says he loves Ubuntu but for some reason it doesn't like me.

I am sure this works in other versions so maybe is there a way to just download updates to the array-1 and install them without logging in - since it won't let me?

Thank you
Colter

---

### Post by Xian on 2005-02-07
The first screenshot with the "Enter a Full Name...." is basically meaningless so we can just ignore that as far login purposes are concerned. 

The second shot looks fine. That should be an acceptable login name and there is no reason it wouldn't be accessible. Check that off.

What I don't like is that third screenshot. What is that space at the front of your password? Is there any chance that you are attempting to enter a number from the right side of your keyboard and those keys are not activated? I mean I'm just tossing out ideas here but no way that space should be there in my opinion. Do you have any further information on this?

---

### Post by blindgoat on 2005-02-07
Yeah - I'm aware the first screen shot is basically pointless but I figured I'd put it there anyway. No - it's not a number. That space is inserted before my password automatically. I even press backspace to try to get rid of it and it doesn't go away. I even tried typing a space when I go to login and that doesnt work either....??? :confused:

---

### Post by Xian on 2005-02-07
That is very strange. My only thought is that perhaps you could do a Ctrl+F1 or such at that point to exit the interface and drop to a command line. Perhaps then you could enter the password correctly. There should be a way to get to a simple prompt, but I'm just not sure if it is Alt or Ctrl + F1, or just a function key by itself. Once there another of the function keys should bring you back. I did that once when I was using parted to make my partitions and wanted to see the command line structure. But I just popped keys until it clicked, not really paying attention to the exact sequence.

Sorry, but I really don't have another idea.

---

### Post by rohandhruva on 2005-02-08
Well, the problem i get with all debian isntaller based installs is, during entering username, it always takes "ohandhruva" if i enter rohandhruva. The first character aint taken. so i need to then boot into recover mode, add a user, and give him sudo previliges. Will hoary have a grpahical install ?

Rohan

---

### Post by Xian on 2005-02-08
Hmmm....it's almost like it is using an incorrect keyboard format.

---

