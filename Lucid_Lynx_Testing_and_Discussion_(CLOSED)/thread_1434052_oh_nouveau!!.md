---
title: "oh nouveau!!"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by wagonfactor on 2010-03-19
(this is inreference to the 10.04 beta 1 that released yesterday)

since this is my first post i guess ill start by saying ive been using linux as my main os for about 8 months or so. ive tried pretty much everything i could get my hands on, mainly through distrowatch. ive always come back to ubuntu because i love the interface, community and its just always worked the best on my computer. i have an alienware m9750 laptop. its an intel duo core 2.16. 2 gigs of ram. with an nvidia geforce 8700m gt 512gigs. im currently running ubuntu 9.10

i was sooo excited when i finally had the beta downloaded and burned. rebooted the comp with it in. it looked really good booting up. the background loads, looks good. i have my little mouse cursor.... and thats it. nothing else happens. the cd eventually stops spinning, my computer doesnt make any noise to indicate that anything is even happening. the exact same thing happens when i try and run fedora, which is why im thinking this is nouveau related. fedora 12 does the same thing 10.04 is doing, but back on fedora 11 i remember getting a nouveau error and a message along the lines of "prepare for strangeness".

im wondering if anyone has encountered this issue or has any suggestions. ive googled just about everything i can trying to come to my own conclusions but i havent really found anything. im really excited about 10.04. ive been talking big things about it to friends and coworkers and now im not even able to install it! any help would be greatly appreciated :)

---

### Post by Sef on 2010-03-19
Moved to Lucid forum.

---

### Post by xebian on 2010-03-19
nouveau == nooboot.

---

### Post by ncubede on 2010-03-20
> **xebian said:**
> nouveau == nooboot.

while I don't like nouveau, that's a bit unfair.  The real issue in my case were all the hosed desktop files in /usr/share/applications, where X-Ubuntu-Gettext-Domain= was at the wrong position.

the below perl script fixed that for me on a root console session, but I assume it may be better to wait for another build.  This one is certainly hosed.

> 
#! /usr/bin/perl

undef $/;

sub read_file {
    open (FILE, "<".shift) || die $!;
    my $content = <FILE>;
    close FILE;
    $content;
}

sub write_file {
    open (FILE, ">".shift) || die $!;
    print FILE @_;
    close FILE;
}

for my $file (@ARGV) {
    print STDERR "$file: ";
    my $content = read_file($file);
    $content =~ s/(X-Ubuntu-Gettext-Domain=.*)\n(\[Desktop Entry\])/$2\n$1/m;
    write_file($file, $content); 
    print STDERR " done\n";
    print STDERR $content;
}



to be run as sudo correct.pl /usr/share/applications/*.desktop

Now I have my desktop back, but I have to agree I need to blacklist nouveau now to get the nvidia proprietary drivers back.  Nouveau is just to slow for me...

---

