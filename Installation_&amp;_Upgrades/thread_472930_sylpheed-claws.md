---
title: "sylpheed-claws"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by neoflight on 2007-06-13
I am using sylpheed now. Could anyone please tell me how to tell this client to save my mailboxes in a folder i specify rather than the default /HOME? .i cant find it anywhere..
thanks...

BTW, its a very fast and excellent mail client...

---

### Post by dannyboy79 on 2007-06-13
there's gotta be a file/folder within your home directory called .sylpheed. within that folder should be the config file you need to edit. I think that if you edit the file after the fact, than retrieve more mail, it may fail if the Mail folder isn't moved or made in the new location that you want your mail stored?? can't say for sure, just a heads up?

the sylpheed folder within your home direcotry which should have the config files within it is hidden, it has a dot at the beginning of it, you can use nautilus or whatever file manager and tell it to show hidden files/folders. that's according to this: [http://sylpheed.sraoss.jp/doc/faq/en/sylpheed-faq-2.html](http://sylpheed.sraoss.jp/doc/faq/en/sylpheed-faq-2.html)

---

### Post by neoflight on 2007-06-13
thanks. I tried looking at various files and could not find the one i need to change or add the path of my new folder into 

the help says what happens..it does not say where to change...

> A. When you run Sylpheed for the first time, it will ask you where you want to store your mailboxes. The default is <homedir>/Mail. You can change this to anything you like as long as it is a valid directory name.

Please note: When Sylpheed is executed for the first time, it automatically creates the configuration files under $HOME/.sylpheed/, and asks you the location of mailbox. The default is $HOME/Mail. If some files which are non-MH format already exist on the directory, you will have to specify another location. 

the strange this is that it didn,t even create the 'Mail' folder at $HOME. I just have all my mailboxes floating around in my home directory. I installed it from the repos. 

Do you know how to accomplish that? the settings? anyone?
ediit: I dont have a config file in $HOME/.sylpheed/ ...:(

---

### Post by neoflight on 2007-06-13
fixed it.. i had to create a folder in the $home directory to give the path while setting the sylpheed up. It was giving me an error when i was giving the path as mymails/myfolder...the mymails folder was not there in the beginning. I created it and it accepted the path.
so its working now. 

it can only create the folder 'Mail' the default.  one. if you want to create a new tree then create the folders and the mailboxes (with the name you chose when configuring) folders will be created inside the custom folder tree...


thanks

---

### Post by savage on 2007-11-27
This setting is contained in an xml file. On my system Ubuntu 7.04 PPC this file was located at $HOME/.sylpheed-claws/folderlist.xml (where $HOME is /home/username/). If you edit this file you will see a line near the top that is similar to this:

<folder name="name-of-folder-holding-your-email" collapsed="0" sort="0" path="folder-holding-your-email" type="mh">

If you want to change the directory where your email is stored, shut down sylpheed-claws first. Create the new directory using the command mkdir, or nautilus file browser. Move your mail folder into this newly created folder.

Next edit the part of the line above path="name-of-new-folder". Sylpheed assumes that the starting directory is your $HOME folder. So for instance you could create a directory called .mail (a hidden directory) and in folderlist.xml it would look like this, path=".mail/folder-holding-your-email".

Now you can start Sylpheed-claws and it should use your new folder path. I hope this makes sense, if not, post, and I'll try to clear it up.

---

### Post by badhat on 2008-02-29
I was able to change the mail directory, by putting the relative path in both accountrc and folderlist.xml . (Absolute paths didn't work, and I found no way to change the meaning of "#mh" .)

---

