---
title: "Script to convert windows .url (internet links) to desktop links for gnome"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by nitromanrc on 2008-08-10
well...the title pretty much says it...I wrote this little script that does that does that... so here it is

```
#!/bin/bash


##A script to convert windows XP (haven't tested other versions) .url files to a desktop website link for gnome. 
##will convert all .url files in the current folder (up to 99, doesn't support 3 digits, however can be edited to do so if needed)
##Written by Dean Lovering
##Feel free to make suggestions, or to improve upon it yourself, send suggestions and improvements to dalovering@gmail.com please.


cat *.url |grep ^URL >> links.tmp # makes a list of all the URLs, and outputs to a temporary file called links.tmp
ls *.url | awk 'BEGIN{FS=".url"}{print $1}' >> names.tmp #makes a list of all the names of the links, and outputs to temporary file names.tmp *the awk command cuts out the ".url" from each one.

if [ $(grep -n U links.tmp | tail -n 1 | cut -c 2) = ':' ] # if last line number (number of links) is one digit
then
	max=$(grep -n U links.tmp | tail -n 1 | cut -c 1) # sets variable $max to equal the number of the last line if 1 digit
else
	max=$(grep http://ubuntuforums.org/archive/index.php/t-436799.html-n U links.tmp | tail -n 1 | cut -c 1-2) # sets variable $max to equal the number of the last line if 2 digits
fi
echo max= $max


line=0
while [ $line -lt $max ]
do 
	line=$(($line + 1))  # sets line number to correct number
	name=$(cat names.tmp | head -n $line | tail -n 1)   # sets $name to equal name of link
#	echo ${name}  #prints name of each link in the shell, used for debugging

	# prints file information into file
	echo [Desktop Entry] >> ${name} 
	echo Version=1.0 >> ${name} 
	echo Encoding=UTF-8 >> ${name}
	echo Name=${name} >> ${name}
	echo Type=Link >> ${name}
	echo $(cat links.tmp | tail -n $line | head -n 1) >> ${name} # $(cat links.tmp |tail -n $line | head -n 1) prints the name of the current link
	echo Icon=gnome-fs-bookmark >> ${name}

done

# give option to delete original .url files
echo "Do you want to delete original .url files <y or n>? \c" 
read del

if [ $del = "y" ] #if user said yes, 
then
	mv *.url ~/.trashes	#move .url files to trash
	echo "You chose to delete original .urls, moving to trash"
elif [ $del = "n" ]
then 
	echo "not deleting originals"	
fi
rm links.tmp # removes temporary files
rm names.tmp
```

---

### Post by VulcanTourist on 2009-11-18
Thank you for taking the time to share this!  This will prove to be an immense time- and frustration-saver for me, since I have many hundreds of .URL files (I wanted to have my links independent of individual browsers).  I discovered these .desktop files in Ubuntu recently, and realized the problem they would pose as I started to seriously consider migrating; I knew this was one minor but very time-consuming thing I would have to address.

Thankfully you've done it for me!  Now, if I can figure out how to use it recursively in a huge directory tree, I'll be ecstatic. :)

---

### Post by davit on 2010-05-08
I made a quick change to the script for URLs I had to change. 

The file extension (URL) was upper-case, it had spaces in file names and needed to change link to a desktop link, using forced '.desktop' extension to modify mime-type or file-type. 


```

#!/bin/bash

##A script to convert windows XP (haven't tested other versions) .URL files to a desktop website link for gnome. 
##will convert all .URL files in the current folder (up to 99, doesn't support 3 digits, however can be edited to do so if needed)
##Written by Dean Lovering
##Feel free to make suggestions, or to improve upon it yourself, send suggestions and improvements to dalovering@gmail.com please.
##
##  Wrapped Url in quotation for spaces and added file extension (.desktop) for mime type - david@mullins.name


cat *.URL |grep ^URL >> links.tmp # makes a list of all the URLs, and outputs to a temporary file called links.tmp
ls *.URL | awk 'BEGIN{FS=".URL"}{print $1}' >> names.tmp #makes a list of all the names of the links, and outputs to temporary file names.tmp *the awk command cuts out the ".URL" from each one.

if [ $(grep -n U links.tmp | tail -n 1 | cut -c 2) = ':' ] # if last line number (number of links) is one digit
then
	max=$(grep -n U links.tmp | tail -n 1 | cut -c 1) # sets variable $max to equal the number of the last line if 1 digit
else
	max=$(grep -n U links.tmp | tail -n 1 | cut -c 1-2) # sets variable $max to equal the number of the last line if 2 digits
fi
echo max= $max


line=0
while [ $line -lt $max ]
do 
	line=$(($line + 1))  # sets line number to correct number
	name=$(cat names.tmp | head -n $line | tail -n 1)    # sets $name to equal name of link
        name=$name."desktop" 
	echo ${name}  #prints name of each link in the shell, used for debugging
        
	# prints file information into file
        echo [Desktop Entry] > "${name}" 
	#echo Version=1.0 >> "${name}" 
	echo Encoding=UTF-8 >> "${name}"
	echo Name="${name}" >> "${name}"
	echo Type=Link >> "${name}"
	echo $(cat links.tmp | tail -n $line | head -n 1) >> "${name}" # $(cat links.tmp |tail -n $line | head -n 1) prints the name of the current link
	echo Icon=gnome-fs-bookmark >> "${name}"

done

# give option to delete original .URL files
echo "Do you want to delete original .URL files <y or n>? \c" 
read del

if [ $del = "y" ] #if user said yes, 
then
	mv *.URL ~/.trashes	#move .URL files to trash
	echo "You chose to delete original .URLs, moving to trash"
elif [ $del = "n" ]
then 
	echo "not deleting originals"	
fi
rm links.tmp
rm names.tmp

```

---

### Post by erkorb on 2010-11-25
This great!  Thank you for sharing this.

But, I found that my first name, was being assigned to my last URL.  So, I had to modify the code to this:

> echo $(cat links.tmp | **[COLOR="Red"]head[/COLOR]** -n $line | [COLOR="red"]**tail**[/COLOR] -n 1) >> "${name}" # $(cat links.tmp |tail -n $line | head -n 1) prints the name of the current link


Erok

---

