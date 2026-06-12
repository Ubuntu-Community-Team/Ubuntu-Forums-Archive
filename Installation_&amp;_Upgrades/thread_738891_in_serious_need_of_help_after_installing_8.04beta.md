---
title: "in serious need of help after installing 8.04beta"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by will61 on 2008-03-29
after installing hardy 8.04 everything seemed to be running just fine however I have 2 major probs 

The first is that I can't empty the garbage bin it gives an error telling me that permission is denied.

The second is more worrying this has to do with firefox3 beta eventhough it's working just fine the problem is that it's not letting me save any settings ,everytime I customise it ,the new settings aren't saved it keeps behaving as if it's the first time it's run each time I start it 

the pproblem with firefox may however be related to something I've done as I did have a failed installation (of fffb4) in gutsy7.10 however the upgrade to hardy 8.04 should have fixed that right ?

any help would be greatly appreciated

---

### Post by TheWizzard on 2008-03-29
try this:
```
sudo chown -R yourname /home/yourname
```

replace yourname with your name ;)
this makes you owner of all the files in your homefolder.

if the problem persists, try:
```
sudo chmod -R 750 /home/yourname
```

---

### Post by will61 on 2008-03-29
Tried both commands still no luck 

the strange thing is when i use nautilus as root (which I do by running "sudo nautilus") and go to my home directory and check the folder "Trash" it's empty and also the Trash folder in the root directory is empty yet "garbage bin" on my Desktop has stuff in it that for some reason I don't have permission to delete

The problem with firefox is solved

---

### Post by petri on 2008-03-30
How did you solve the Firefox problem?

BTW, it is recommended to use gksu instead of sudo when starting a program with graphical interface. For example sudo firefox can mess up your ICEAuthority and you can't login. Happened to me a couple of years ago.

---

### Post by kane77 on 2008-03-30
> **will61 said:**
> Tried both commands still no luck 

the strange thing is when i use nautilus as root (which I do by running "sudo nautilus") and go to my home directory and check the folder "Trash" it's empty and also the Trash folder in the root directory is empty yet "garbage bin" on my Desktop has stuff in it that for some reason I don't have permission to delete

The problem with firefox is solved
did chowning your home directory help to make firefox remember settings/logins? I have the exact same problem.. I log in to some page and check keep me logged in but next time I come back i need to log in again and it doesn't even remember passwords although I set it so.

---

### Post by TheWizzard on 2008-03-30
try the command line: 
[http://www.howtogeek.com/howto/ubuntu/how-to-empty-the-ubuntu-gnome-trash-from-the-command-line/](http://www.howtogeek.com/howto/ubuntu/how-to-empty-the-ubuntu-gnome-trash-from-the-command-line/)

---

### Post by will61 on 2008-03-30
My solution to my firefox problem is as follows 

Firstly I'll explain that it probably was self inflicted (my own fault) that it messed up in the first place ,because I had tried to install it before I had upgraded to 8.04 hardy 

My problem with firefox was caused by an extracted archive of firefox that I had downloaded and every time I launched firefox it would launch from the extracted archive instead of the installation directory and because it was launching form the extracted archive it would behave as if it was first run on every launch and not save any previous settings 

I solved the problem by uninstalling firefox using synaptic performing a "complete removal" and then logging onto nautilus as root ("do this by running the command sudo nautilus") and then from there you manually delete every last trace of firefox in the "etc" directory you will find a firefox folder just delete it and in your home folder you will find a hidden folder called "mozilla" you will have to enable "show hidden folders" to see it 

once you've done all this do a fresh install of firefox and it should run just fine well at least for me it did I hope this helps for those who asked I'm sure there's a quicker way of doing this but I'm not that experienced with linux yet.

---

### Post by will61 on 2008-03-30
try the command line:
[http://www.howtogeek.com/howto/ubunt...-command-line/](http://www.howtogeek.com/howto/ubunt...-command-line/)
_______________

Thanks for the help but that didn't work

---

