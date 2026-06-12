---
title: "Thunderbird dependency issue?"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by strungoutfan78 on 2007-05-25
HI.  I just reinstalled kubuntu due to a vmware incident:(  Now i can't seem to install Thunderbird again.  It was fine before, but this time it keeps telling me i need libplds4.so.  The outcome is the same if I install mozilla-thunderbird or just thunderbird.  Also if i use the gui or from the console.  It appears to install correctly and gives me no flags or warnings.  Here is my output when i try to run it:

neil@neil-laptop:~$ thunderbird
/usr/lib/thunderbird/thunderbird-bin: error while loading shared libraries: libplds4.so: cannot open shared object file: No such file or directory

I've searched on these forums and googled it and I can't seem to find anything in reference to this particular problem.  Oh and yes I'm sure I could just compile from source but I really don't want to if I can avoid it.  I've gone that route before and I've come to realize that if I stick to the package manager as much as possible it just keeps things alot neater.  Any advice here would be greatly appreciated.  Thanx;)

---

### Post by strungoutfan78 on 2007-05-25
Ok.  So I found libplds4.so.  It's in /usr/lib/swiftfox/plugins.  When I discovered this I came to the natural conclusion that Thunderbird was probably looking for this module in /usr/lib/firefox/plugins.  Unfortunately after creating a symlink to it in /firefox/plugins  still gave the same outcome.  I also tried a symlink in /usr/lib/thunderbird (not /usr/lib/thunderbird, as that directory does not exist) but still nothing.  I need to find out where it's looking for this module.  And god forbid once it finds this one it starts looking for another and so on.

Another question.  I chose not to install firefox when i reinstalled kubuntu.  Maybe if I install it everything will magically be in the right location?  Probably not.  It appears that all the necessary firefox directories were installed with swiftfox. :confused:

---

### Post by strungoutfan78 on 2007-05-25
Ok so I took my own advice and installed firefox and oila... thunderbird works.  Shouldn't this be a dependency issue that apt has somehow missed?  I've been impressed thus far with the adept package manager but this one seems way too blatant.

I stilll have one small issue.  When i open the add-on dialogue in thunderbird and click "get themes" or "get extensions" nothing happens.  I can live with this as long as I can go to to the website and download them myself still.  Wierd.

Kinda feels more like a blog, doesn't it?  I'll keep you all posted!;)

---

### Post by strungoutfan78 on 2007-05-26
Ok so it's not just the add-on dialogue.  It's everything.  I can't open any links from Thunderbird.  What gives now?:confused::confused:

---

### Post by strungoutfan78 on 2007-05-27
Seems neither firefox or swiftfox can pick up hyperlinks from thunderbird, and vice-versa.  I don't get it.

---

### Post by strungoutfan78 on 2007-05-27
OK.  I downloaded Thunderbird and installed from the Mozilla website.  Same deal.  I think I'll just start digging my eyeball]s out with a fork now.](*,)

---

### Post by strungoutfan78 on 2007-05-27
I finally ran across a solution in my searches through the forums.  Seems it had to come in two parts though.

Part 1. - enabling swiftfox/firefox to open mail:to links

Solution found here [http://ubuntuforums.org/showthread.php?p=959382]("http://ubuntuforums.org/showthread.php?p=959382") post#9
Worked like a charm.

Part 2. - enabling Thunderbird to open hyperlinks in a swiftfox/firefox window/tab

Solution found here [http://ubuntuforums.org/showthread.php?t=60427]("http://ubuntuforums.org/showthread.php?t=60427")
Make sure to pay close attention to the fact that thunderbird and firefox must not be running when making these changes.  It will reset the file upon closure.  It happened to me.

After beating my head against the wall with this issue, I began to wonder something.  Let me start off by saying tthat I am, by no means, an expert with Linux nor will I ever claim to be.  It seems to me though, that every time I install/reinstall the same distro, from the same media, with the same options, I always get some new, wierd issue that was not there in the previous install.  Why such an inconsistency? 

I've used several different distros and I have at one point or another had to reinstall every one of them.  And everytime I came up with some weird new problem that wasn't there previously.  This problem was no exception.

Again, thanx to this community for helping solve this problem.  Even though no one posted here I was still able to find my answers.
Cheers!:guitar:

---

