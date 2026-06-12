---
title: "Will a Ibex install on my machine delete my home folder?"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by vishnumrao on 2008-10-28
I am running Ibex since alpha 3. My current install started at Fiesty Fawn -> Gutsy -> Hardy-> Ibex.

I was thinking of doing a complete reinstall of Ibex when it comes out on 30th. (Just to get rid of all the extra stuff that I have installed over time and also to do away with all the customization)

Will a reinstall of Ibex overwrite my home folder or will it retain my home folder structure and its contents?

---

### Post by Partyboi2 on 2008-10-28
If your /home folder is on its own partition then you should not lose the contents of  /home. If you have not got your /home on its own partition then you can follow [[COLOR=Blue]this[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome") to do so. Then when you get to the partition stage of the install choose "Manual" and tick the box to format your / partition (don't tick the box for /home or you will lose your data) and reset the mount point for your /home partition to /home.

---

### Post by vishnumrao on 2008-10-29
My /home folder is not in its own partition. I do not have seperate partition. My Ubuntu install uses the entire drive. 

Thanks for your input. For my case, will a Ibex install on my machine delete my home folder?

---

### Post by rideburton56 on 2008-10-29
Would it not be possible to have the /home folder to be on a usb drive or something along those lines?

---

### Post by stimpak on 2008-10-29
this is the easy way out - copying your /home while you reformat everything. what happens if you dont have a usb drive or a choice of writing your /home somewhere safe?

---

### Post by ad_267 on 2008-10-29
Yes reinstalling with 8.10 would overwrite your home directory.

You can put it on a separate partition or back up your data to something like a usb drive before installing.

---

### Post by battleshipterry on 2008-10-29
I am new at this but if you reinstall and have been able to save /home then I have had a permission problem accessing the folder after the reinstall.Ubuntu would not let me see in the folder it said I did not have permission.Remember I am a newbee at this.

---

### Post by vishnumrao on 2008-10-29
> **stimpak said:**
> this is the easy way out - copying your /home while you reformat everything. what happens if you dont have a usb drive or a choice of writing your /home somewhere safe?

Copying about 400GB of stuff to a usb would require me to have another 500GB drive or more. And would take hours to do the copy to external and later after install hours to copy back. LOL.

---

### Post by ad_267 on 2008-10-29
Sorry I don't quite understand your problem. Is your /home a separate partition? And you reinstalled and left your home partition as it is?

Then yes the permissions will need to be updated. You can do this for all your users from a terminal. Replace USERNAME with each username:

```

sudo chown -R USERNAME:USERNAME /home/USERNAME

```

---

### Post by rideburton56 on 2008-10-29
> **stimpak said:**
> this is the easy way out - copying your /home while you reformat everything. what happens if you dont have a usb drive or a choice of writing your /home somewhere safe?

It seems to me that there are only two ways around this, seperate partition or external data source?

---

### Post by kstella on 2008-11-26
> **ad_267 said:**
> Sorry I don't quite understand your problem. Is your /home a separate partition? And you reinstalled and left your home partition as it is?

Then yes the permissions will need to be updated. You can do this for all your users from a terminal. Replace USERNAME with each username:

```

sudo chown -R USERNAME:USERNAME /home/USERNAME

```

Just to check, the first username is my username under Hardy, and the second and third are my username under Ibex? Or are the first and third the same?

---

