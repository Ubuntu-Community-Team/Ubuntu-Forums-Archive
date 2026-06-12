---
title: "update to banshee 1.5.1 corrupts database"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hanlin on 2009-10-11
I just got an update, and updated banshee to 1.5.1. However, it corrupted my database. Every song now shows up as Unknown artist and Unknown album, although the title still shows up properly. If I attempt to play a song, it will quit immediately. Any ideas?

---

### Post by pouk-ledden on 2009-10-11
Ditto here, except mine doesn't crash -- it just doesn't play any music. When I try to play anything, I get this pop-up: 

"Problem with Player Engine

Object reference not set to an instance of an object"

I do kinda wonder why they are pushing through a what is actually a beta, and a first beta at that. This version, for instance, isn't in the Stable PPA for Banshee. I'd think it would be better to stick with the stable version as far as Ubuntu's repositories are concerned.

---

### Post by FuturePilot on 2009-10-11
> **pouk-ledden said:**
> Ditto here, except mine doesn't crash -- it just doesn't play any music. When I try to play anything, I get this pop-up: 

"Problem with Player Engine

Object reference not set to an instance of an object"

I do kinda wonder why they are pushing through a what is actually a beta, and a first beta at that. This version, for instance, isn't in the Stable PPA for Banshee. I'd think it would be better to stick with the stable version as far as Ubuntu's repositories are concerned.

My guess is that Banshee is very close to the 1.6 release so they put the Beta release in the repos so that it would be a minor update to the final 1.6 release and can be considered for an SRU.

---

### Post by pouk-ledden on 2009-10-11
Aha! Got it working!

Delete your database. I just went ahead and deleted the Banshee config folder in .config and in .gconf/apps  -- I'm not sure if it's necessary to do both, or if one or the other is the real one. Then rebuild the database from scratch.

Downside, of course, is losing anything you had set up -- playlists, ratings, podcasts, etc. But at least I can listen to music again!

---

### Post by hanzomon4 on 2009-10-11
Is lastfm [plugin working again]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/430473")

---

### Post by pouk-ledden on 2009-10-11
Nope, the Last.fm plugin doesn't load stations for me. It scrobbles, it recs, but no stations. Sigh...

---

### Post by hanlin on 2009-10-11
I don't really want to lose my song ratings or play counts. Is there a way to revert back to 1.4.3? The banshee PPA doesn't seem to have that for karmic.

---

### Post by pouk-ledden on 2009-10-11
> **hanlin said:**
> I don't really want to lose my song ratings or play counts. Is there a way to revert back to 1.4.3? The banshee PPA doesn't seem to have that for karmic.
Sadly, I don't think so. When the Karmic PPA finally has the stable version, though, you can add that and then force the earlier version (package > force version in Synaptic, with Banshee selected). Until then, though. And maybe the next update of this beta version will fix the problem. *fingers crossed*

I poked around the banshee setting folder. Sadly, it looks like most everything is probably in the .db file in there. So it's probably all or nothing with that route.

---

### Post by hanlin on 2009-10-12
I wrote a little perl script to update the old database to the new one, and it works quite well for me. It definitely isn't elegant though, and you do have to do some manual processing of the files.

Here's what you have to do:
1. install sqlite3
2. terminal: sqlite3 /path/to/banshee.db ".dump" > dump_1.4.3
3. move banshee.db to somewhere else, open banshee, and reimport all your music.
4. terminal: sqlite3 /path/to/banshee.db ".dump" > dump_1.5.1

So now we have 2 dump files, one for the old library, and one for the new library.

5. move the script and the 2 dump files to the same directory.
6. open up the 2 dump files, and replace ', ' with '!@#' and replace ',%20' with '!@#@!'. Since we are processing the file using a comma as the separator, we need to replace all the commas with something else. Now if you have a name with a comma with no space afterwards, then you'll gonna have to fix that first.
7. run the script. Note that this script matches song title and genre, so if you have 2 songs with the same name and same genre, then the 2nd one will have the playcount and ratings of the first one.
8. now that you have created a new file named dump, you need to go into the file and replace '!@#@!' with ',%20' and '!@#' with ', '
9. terminal: cat dump | sqlite3 banshee.db. If you get errors, this is where it'll tell you. Make sure to delete the banshee.db file before each time you run this.
10. now move it into ~/.config/banshee-1/ and you're done

Like I mentioned, there are some limitations to this. You can't have commas in titles, comments, etc without a space after it. Also, you can't have comments with multiple lines. You either need to fix it manually in both dump files first, or you're gonna have to edit the script to deal with it. Finally, if you have a song with the same name and genre, you're gonna have some minor issues.

I hope this'll help others out there like me until banshee fixes the issue.


```
#!/usr/bin/perl

$file_143="dump_1.4.3";
$file_151="dump_1.5.1";

open(newDB, ">dump");
open(FILE_151, $file_151);

while(<FILE_151>){    #loop through new database
    if (/INSERT INTO \"CoreTracks\" VALUES/) {
        @line1=split(',', $_);
        $begin=join(',',@line1[0..29]);
        $end=join(',',@line1[38..$#line1]);
        
        $title_new=@line1[13].@line1[23];    #title of song+genre
        $title_old='';
        
        open(FILE_143, $file_143);
        while(<FILE_143>) {    #loop from old database to find the matching title+genre
            if (/INSERT INTO \"CoreTracks\" VALUES/) {
                @line2=split(',', $_);
                $title_old=@line2[14].@line2[22];    #title of song+genre
                if ($title_old eq $title_new) {
                    $data="@line2[29]".",0,".join(',',@line2[30..35]);
                    print newDB "$begin,$data,$end";
                    last;
                }
            }
        }
        close FILE_143;
    }
    else {
        print newDB "$_";
    }
}

close newDB;
close FILE_151;
```

---

### Post by gabaug on 2009-10-13
When you get a crash or corruption in an application, you should file a bug on launchpad.net (or directly on the upstream project's bug tracker).

There should not have been a problem with the database upgrading to 1.5.1 - it's not something the developers (myself included) are aware of or have seen.  The only way we can fix it for you and others is to get more information.  Can somebody who is seeing this issue and willing to help us resolve it file a bug?  Thanks!

---

### Post by sirgogo on 2009-10-22
How did you guys update to 1.5.1? Mine is stuck on 1.4.3. I was hoping it would update through synaptic. Not sure what's going on.

---

### Post by Surfrock66 on 2009-10-25
> **gabaug said:**
> When you get a crash or corruption in an application, you should file a bug on launchpad.net (or directly on the upstream project's bug tracker).

There should not have been a problem with the database upgrading to 1.5.1 - it's not something the developers (myself included) are aware of or have seen.  The only way we can fix it for you and others is to get more information.  Can somebody who is seeing this issue and willing to help us resolve it file a bug?  Thanks!

I've never submitted a bug, what info is useful, what do I do?  I'm happy to submit and I'm getting this error, I just don't really know how.

---

