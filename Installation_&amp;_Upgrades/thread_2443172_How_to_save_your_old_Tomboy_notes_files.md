---
title: "How to save your old Tomboy notes files"
date: 2020-05-12
forum: Installation &amp; Upgrades
---

### Post by hsweet2 on 2020-05-12
I have a bunch of old Tomboy notes I need occasionally and found the program is gone from repositories and did not follow my upgrade.  The following is instructions on how to save and re-use Tomboy notes.

The notes are text/xml files and  are located in ~/.local/share/tomboy and have  long hex names with a .note extension.  I used sed to remove most of the unneeded xml and a short perl script to rename all the files from c9a88dec-58ee-4f29-a1d6-155008cceb1b.note to the title text from the note.  So that might become something like "How to fix Blender.txt"

Copy all the .note files to a new folder.  Or make a backup of the folder as all the files will be modified.
From a terminal window in the folder with Tomboy files...  This will remove at most of the unneeded XML.  You might want to run the $d line a few times.  It will remove the last line each time you run it.  

```

sed -i '1,2d' *.note
sed -i '$d' *.note
sed -i '/<last/d' *.note 
sed -i '/<create/d' *.note 
sed -i '/</note/d' *.note 
sed -i '/<\/note/d' *.note 
sed -i 's/<title>//' *.note
sed -i 's/<\title>//' *.note
sed -i 's/</title>//' *.note
sed -i 's/<\/title>//' *.note
sed -i 's/^[ \t]*//' *.note 

```
Check a couple of files to make sure sed did the job.. 
Then you can rename all the files with this perl script
```

use File::Path; 
use strict; 
use feature ':5.10'; 
  
#rename old tomboy notes using the title as the new file name 
#make a backup of originals before running this! 
  
my ($original_type);   
my $path = '/home/hxxxx/Desktop/tom';   #path to the backup folder 
  
#***************************  end of setup ******************* 
         
opendir(NOTES,$path) || die "$path is not a valid directory: $!";  
my @files=grep(/note/, readdir NOTES);    #filter by file types  
 
 
foreach my $original(@files){ 
    my ($base_name, $ext)=split(/\./,$original); 
    open(MYFILE, $original ) || die "opening $original: $!"; 
        my $title=<MYFILE>;     #read title line only 
    close(MYFILE);   
    chomp $title; 
    my $new_name= $title.".txt"; 
    rename $original, $new_name; 
} 


```

I could have done it all in perl, but this was quicker for a one timer : )

---

### Post by erind on 2020-05-12
> **hsweet2 said:**
> I have a bunch of old Tomboy notes I need occasionally and found the program is gone from repositories and did not follow my upgrade.  The following is instructions on how to save and re-use Tomboy notes.

The notes are text/xml files and  are located in ~/.local/share/tomboy and have  long hex names with a .note extension.  I used sed to remove most of the unneeded xml and a short perl script to rename all the files from c9a88dec-58ee-4f29-a1d6-155008cceb1b.note to the title text from the note.  So that might become something like "How to fix Blender.txt"

[...]


Thanks hsweet2 for your efforts, it'll come in handy.... I don't like when notepads' software save their notes in hard-to-parse format.

---

### Post by dragonfly41 on 2020-05-12
I use [cherrytree edito]("https://www.giuspen.com/cherrytree/")r extensively and although I have not used this feature you can import Tomboy notes.
Cherrytree can import a bunch of other formats.
In fact I also retain Tomboy notes.

---

### Post by Irihapeti on 2020-06-06
If you still want to use a note application like Tomboy, the notes can be imported into Gnote. Gnote looks very much the same as Tomboy. (At least, if my old memory is good enough, for it's some years since I used Tomboy.)

Gnote has the import plugin installed by default, so it should be a fairly straightforward process.

---

