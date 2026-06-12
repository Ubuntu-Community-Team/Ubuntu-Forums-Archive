---
title: "adding Copy To &amp; Move To within right-click context menu PCManFM"
date: 2014-06-23
forum: Installation &amp; Upgrades
---

### Post by roler2 on 2014-06-23
Is there a way to add Copy To & Move To within the right-click Context Menu of PCManFM running Lubuntu 14.04? I read something about adding an executable bash file but I would not know how to do that. I don't remember where I read about that. It was confusing to me anyway. I know you can go to Edit on the Menu however I wanted to try and see if it is easier to utilize the Context Menu to Copy and Move. Is there is a ready-made script to add these two commands?

Any assistance would be greatly appreciated. Thank you!

---

### Post by bapoumba on 2014-06-24
Not sure how easy this could be as I guess you wont be moving to the same file/directory each time, am I right ? You'd need a dialog box on top of the right click item.
Best is, imho, cut & paste (that will move) or copy & paste (that will keep the original file).

---

### Post by Dennis N on 2014-06-24
I believe this would be done through PCManFM's  **custom actions**.

[http://lubuntublog.blogspot.com/p/actions_24.html](http://lubuntublog.blogspot.com/p/actions_24.html)

Unfortunately, I find madebits blog entry linked to in the lubuntu blog is no longer accessable (I get 403-forbidden). There were several ready to use custom actions there some time ago. You would have to do more searching on the web on this topic. I will see what I can find.

---

### Post by roler2 on 2014-06-24
I believe that is the website (Madebits) that I found some confusing instructions. I also receive a 403-forbidden. If you find anything that can be applied I would very much appreciate your assistance. Thank you.

---

### Post by bapoumba on 2014-06-25
May be here : [http://igurublog.wordpress.com/downloads/mod-pcmanfm/](http://igurublog.wordpress.com/downloads/mod-pcmanfm/) - ubuntu ppa here : [https://launchpad.net/~mati75/+archive/spacefm](https://launchpad.net/~mati75/+archive/spacefm) but I have not tested (had bookmarked the lubuntu wiki page for later use..), but looks like it is a fork and not PCManFM itself.

---

### Post by roler2 on 2014-06-26
The second link is the updated PCManFM modification however the development has been suspended as of April 2014:

**[COLOR=red]ANNOUNCEMENT 2014-04-28[/COLOR]: Most development and maintenance on the SpaceFM and udevil projects is indefinitely suspended. See [IgnorantGuru's Hiatus]("http://igurublog.wordpress.com/2014/04/28/ignorantgurus-hiatus/")     **[http://ignorantguru.github.io/spacefm/](http://ignorantguru.github.io/spacefm/)

I left a message on the Lubuntu Blog link posted by Dennis N. above regarding the 403-Forbidden message however I have not received a reply as of this specific reply posting.

---

### Post by bapoumba on 2014-06-26
Yes, but they still have a Trusty and an Utopic archive in the ppa.

---

### Post by roler2 on 2014-06-27
I have been able to access the instructions to add Copy To. It appears the 403-Forbidden has been fixed. If anyone can be of assistance I would really appreciate it. How do I make the file executable? Do I utilize Leafpad to copy the code? How do you utilize the script and add Move To? Do I replace cp -r with mv and utilize the same script? Where do I place the .sh file as I do not have a folder called bin under the home directory. The only bin folder is under the root directory.

**Copy To Folder**: Thefollowing local action copies the selected file or folder to anotherfolder selected graphically via zenity.


First, create a bashscript called copytofolder.sh in your ~/bin folder with the followingcontent and make the file executable:


#!/bin/bash


folder=$(zenity--file-selection --directory --title="Copy To Folder")
if [[ $folder ]];then
	# cp -r $@"$folder"
	for var in "$@"
	do
	    cp -r "$var""$folder"
	done
fi


Then create thefollowing copy-to-folder.desktop custom menu action:


[Desktop Entry]
Type=Action
ToolbarLabel[en_US]=CopyTo Folder
ToolbarLabel[en]=CopyTo Folder
ToolbarLabel[C]=CopyTo Folder
Name[en_US]=Copy ToFolder
Name[en]=Copy ToFolder
Name[C]=Copy ToFolder
Profiles=profile-zero;


[X-Action-Profileprofile-zero]
Exec=/home/username/bin/copytofolder.sh%F
Name[en_US]=Defaultprofile
Name[en]=Defaultprofile
Name[C]=Defaultprofile


Replace usernamewith your user name. This action will copy all selected files andfolder (hence %F) to another folder of choice. You can define asimilar action Move To Folder by having a similar script using the mvcommand rather than the cp -r one.

---

### Post by roler2 on 2014-06-27
How do I make the script executable? I was able to get Copy To within the Context Menu but it does not work.

I utilized this command: sudo chmod u+x /bin/copytofolder.sh but it did not make the script executable. It still shows as a "shell script" within the /bin Folder.

Thank you for any assistance.

---

### Post by Dennis N on 2014-06-27
> **roler2 said:**
> How do I make the script executable? I was able to get Copy To within the Context Menu but it does not work.

I utilized this command: sudo chmod u+x /bin/copytofolder.sh but it did not make the script executable. It still shows as a "shell script" within the /bin Folder.

Thank you for any assistance.

The script should be in ~/bin, not /bin. ~/bin does not exist by default. You have to create it in your home folder.
To make the script in ~/bin executable:
```
chmod +x ~/bin/copytofolder.sh
```
The command in the Exec= line may be wrong as well. Hard to tell unless you post your actual desktop file with code tags around it for clarity. 

It should be (with your actual user name substituted for username):
```
Exec=/home/username/bin/copytofolder.sh %F
```
Note the space between sh and %F -- it's missing in your post.

(In the future, you should put code tags around any computer code to be sure it is clear the reader.)
------------------------------------------------------------------------------------

To check it out myself, I downloaded the .deb file **madebits-pca_1.0.0-1.deb** that he offers and got "copy to" to work by extracting the two necessary files from it. 

First impressions:
It works, but needs improvements. The save to dialog is too large, doesn't open to the last location used, doesn't add locations used to the Recent Places list, doesn't remember its window size after resizing and doesn't warn you if you have files of the same name in the destination - it always replaces files. As is, not what I would really want to use.

---

### Post by roler2 on 2014-06-28
Thank you so much for the information. I really appreciate it. I notice in home/username that all the folders have a period in front of the folder- .config, .cache, .gnome etc. Do I put a period in front of the newly created bin folder? Is it .bin or just bin without the period in front?

---

### Post by Dennis N on 2014-06-28
> **roler2 said:**
> Thank you so much for the information. I really appreciate it. I notice in home/username that all the folders have a period in front of the folder- .config, .cache, .gnome etc. Do I put a period in front of the newly created bin folder? Is it .bin or just bin without the period in front?

Just some folder names begin with a period. This makes them hidden folders - you can hide them from showing in the file manager. ~/bin is not a hidden folder, so don't use a period. To toggle viewing hidden folders view on and off, you can use keys ctrl+h when viewing in the file manager. Observe that Documents, Downloads, Pictures, and others don't have a period and are not hidden.

Another option for you:

If you want to save some time, you could download the file madebits-pca_1.0.0-1.deb from [http://madebits.com/blog/?x=entry:entry140317-141947](http://madebits.com/blog/?x=entry:entry140317-141947) and take his suggestion of installing with the gdebi package installer. Everything will get copied to its proper location and set up automatically. Plus you get 8 additional custom actions.

On  the other hand, what you are doing is a learning experience. Your choice.

---

### Post by roler2 on 2014-06-29
Thank you once again for all of your assistance. I actually did get the script to work. So now Copy To does work within the Context Menu. It may not perfect and it is a little slow but I am happy with the function as I can copy any file or folder to any other file or folder, or at least I was able to do so with the script. Now I am attempting to see if I can get Move To activated. Is this correct for the Shell Script-I replaced cp -r with mv

#!/bin/bash


folder=$(zenity --file-selection --directory --title="Copy To Folder")
if [[ $folder ]]; then
	# mv $@ "$folder"
	for var in "$@"
	do
	    mv "$var" "$folder"
	done
fi

Thank you again. I could not have done this without your help!

---

### Post by Dennis N on 2014-06-29
Yes, that is what the blog said to do as I recall - replace **cp -r** with **mv**. I would change the --title in the script you show, to "Move to Folder". This is what shows up on the title bar of the popup window. Be sure the .desktop file has the right name in it as well.

Give it a test on a file and see what happens.

---

### Post by roler2 on 2014-06-29
Thank you so much again for your valued assistance! I was able to get the Move To script to work! Now both Copy To and Move To work within the Context Menu. Now I wish there was a way to sort the Context Menu alphabetically as Move To is above Copy To within the Context Menu and Open Folder is at the end. Thank you again. I really appreciate the assistance.

---

### Post by bapoumba on 2014-06-30
If you got to a working solution, please mark your thread as solved (under Thread tools), thanks.
And thanks to Dennis N :)

---

### Post by roler2 on 2014-06-30
Should I then post my new question regarding sorting the Context Menu in another separate post?

---

### Post by roler2 on 2014-06-30
I cannot say my solution will work for everyone. The solution is not perfect although somewhat functional. It does work for me but for others it may not be suitable.

---

### Post by bapoumba on 2014-06-30
Well, it is up to you. Not sure there is a better solution anyway.
I think it is better to keep your other questions to a new thread not to mix up things. If you want people who subscribed here to see it, you should post a link once the new thread is created.

---

### Post by roler2 on 2014-07-01
OK then I will mark this thread as solved. Just as long as anyone else who attempts the solution knows that it may not work perfectly for them. I will do a separate post about trying to sort the PCManFM Context Menu, if that is possible to do.

Thank you again for all of the assistance.

---

