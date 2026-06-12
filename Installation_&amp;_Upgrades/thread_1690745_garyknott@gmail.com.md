---
title: "garyknott@gmail.com"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by knott9 on 2011-02-18
Dear forum readers,  

1. I want to get a ubuntu cd (not dvd).  Where do I go on the web to have
it mailed to me (not an iso download, but a real cd)?

2. I have an old PC with redhat 8 and windows dual-boot.  I want to
destroy and format as ext3 my windows partition (whatever it is -RH8 does
not know about it,) and put a new ubuntu system there using my existing
RH8 home partition.

3. I do not want a new grub installed - I want the ubuntu
OS image placed in my existing boot partition, and I want
to tell my old grub how to offer this new ubuntu as a boot option
along with my old RH8 option. (I will need to remove my 
old windows boot option.

I expect I will need to use fdisk and/or gparted, and edit
some grub file (with emacs).  I would like to do all the prep
work using RH8, and then stick in the ubuntu cd and tell it the
right things, whatever they are, to change ONLY the newly
reformatted partition that used to hold windows (and add to my boot
partition).

Before I can use fdisk, I need to find-out and write-down
what my partitions are, what RH8 mounts, and how to
tell my new ubuntu what partitions to mount, especially my
old home and an ancillary second disk mounted as /sto in
RH8.

The reason I want to install ubuntu is that my old firefox
does not work on many web-sites, especially google, and it
seems to be impossible to install a newer browser because
my .so files (equivalent to .dll's I think) are all too old to work
with new software (is the C runtime library, 
the X-windows glib file, or what, that is too old?
I am unsure what is dynamically linked, and how to find out.  

- I wish programs came as self-contained
binaries, at least as an option, that would solve the old OS and
supporting files problem which is a huge problem.

I will appreciate any detailed help.  I think I know what I
want to do but I don't know the programs or commands
that get it done.  I am very afraid of answering questions to direct
an installer program without understanding what is
happening.

Thanks, [EMAIL="garyknott@gmail.com"]garyknott@gmail.com[/EMAIL]  

(By the way, I am not sure how to
see any answers that might be posted.  I guess I login to ubuntu forums,
and do a search for some word like garyknott that i used in this post.
Is there another more civilized way? - my own opinion is that a mailing-list
kind of option for forums would be helpful, but I guess that would generate
too much email when one has more than a few thousand users. )

[I noted that I used my email address where I should have entered a topic title.
But, editing this post does not allow me to change the title of the thread.  I
guess that makes sense.]

---

### Post by oldos2er on 2011-02-18
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

To specify an installation partition, use the manual installation option. I would really encourage you *not* to use your current RH8 home partition as Ubuntu's home partition if you wish to continue to use RH8, since there have no doubt been a great many changes in Ubuntu's up-to-date default applications compared to RH8's.

Edit: To see your posts, click the dropdown 'Search' menu at the top of the page, Find all my threads/Find all my posts.

---

