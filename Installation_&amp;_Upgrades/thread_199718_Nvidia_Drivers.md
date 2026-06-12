---
title: "Nvidia Drivers"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by cabber on 2006-06-19
Using Dapper 6.06 trying to install latest Nvidia 8762 drivers.  

I'm using this method: ```
1) Download the script

(right click on "envy_8756_32" or  on "envy_8756_64" or  on "envy_8756_32_breezy" or  on "envy_8756_32_breezy" and select "Save link as..." and save it to your harddisk)

2) Log out and press CTRL+ALT+F1 (so as to get out of the Desktop Environment, i.e. you'll see ONLY the command line)

3) Log in (if required)

4) Make the script executable:

cd /home/your_username/path_to_the_file_you_downloaded

sudo chmod a+x name_of_the_file_you_downloaded

5) Run the script:

sudo ./name_of_the_file_you_downloaded

```

I right click on the proper file, save it in my home folder, but cannot get the proper path set in step 1.  
user name: chop
file name: envy_8762_32

When I hit CRT ALT F1, I log in and follow step 1.  It states no such directory.  What am I missing?

---

### Post by localzuk on 2006-06-19
Well, it depends where you have saved it to. Did you save it in to your home directory? Or did you save it on to the desktop?

The path only needs to reflect the actual place where the file resides.

---

### Post by tseliot on 2006-06-19
[QUOTE=cabber]Using Dapper 6.06 trying to install latest Nvidia 8762 drivers.  

I'm using this method: ```
1) Download the script

(right click on "envy_8756_32" or  on "envy_8756_64" or  on "envy_8756_32_breezy" or  on "envy_8756_32_breezy" and select "Save link as..." and save it to your harddisk)

2) Log out and press CTRL+ALT+F1 (so as to get out of the Desktop Environment, i.e. you'll see ONLY the command line)

3) Log in (if required)

4) Make the script executable:

cd /home/your_username/path_to_the_file_you_downloaded

sudo chmod a+x name_of_the_file_you_downloaded

5) Run the script:

sudo ./name_of_the_file_you_downloaded

```

I right click on the proper file, save it in my home folder, but cannot get the proper path set in step 1.  
user name: chop
file name: envy_8762_32

When I hit CRT ALT F1, I log in and follow step 1.  It states no such directory.  What am I missing?[/QUOTE]
Try step 4 and 5 in the following way:

4) cd $HOME

sudo chmod a+x envy*

5) Run the script:

sudo ./name_of_the_file_you_downloaded

---

### Post by Gustav on 2006-06-19
Look at this for installing nvidia drivers: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by cabber on 2006-06-19
Got it.  Thanks guys that worked.  So what is the easiest GUIDE to install xgl and compiz with the Nvidia 8762 drivers and a fresh install of Dapper?  Thanks again.

---

### Post by FredB on 2006-06-19
If someone post this guide, I would be grateful too... Or will I wait until Edgy is released in next october ? ;)

---

