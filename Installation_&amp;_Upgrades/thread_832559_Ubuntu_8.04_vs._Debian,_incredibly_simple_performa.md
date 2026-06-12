---
title: "Ubuntu 8.04 vs. Debian, incredibly simple performance oriented face-off"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by rsaavedra on 2008-06-17
Hello all,

I'm new here but have been trying several linux distros in a few machines, and wanted to share a simple experiment that surprised me quite a bit today.  The post is long, hope you are patient enough to go through all of it.  There's really nothing deep in this post, actually, you'll be rather amazed at how elementary my experiment was.

I've been using Ubuntu since last year (v7.10) on a rather powerful machine with 2GB of RAM and a Core 2 duo Intel CPU.  But recently at work I came across an old Compaq laptop (Evo N610c) that only has 256 MB of RAM.  I decided to try some Linux distros on it to see how they did.

I know Ubuntu recommends more than 256MB of RAM, in particular for running OpenOffice, but I decided to install Ubuntu because it's the one distro I'm most familiar with.  Then decided to install also Debian (with the netinst CD) using Gnome as window manager.  The idea was to use Debian as some kind of baseline to compare Ubuntu 8.04 with.  After this I would probably try some other distros.

So this low-end laptop has now both distros in dual boot mode: Ubuntu 8.04, and Debian.  Each distro has its own 8 GB partition for "/"; both distros share the swap partition (512 MB), and there is one single 8 GB partition that both systems mount at "/home". I'm hoping this is not a problem, haven't seen any yet, except for a default browser question when swiching systems.

The distros installed without any hitch.  After installation, I had both systems download their updates to the latest, so that both report system updated with no updates pending.  (This comparison was done earlier this morning, so Firefox 3 hadn't been released).


One purpose of my experiment/test is to simply compare both distro's performance and behavior for a total newbie end user, using the apps each distro brings for the same tasks, whatever the differences between those apps might be in weight and features, as far as they are intended to do more or less the same thing.  Maybe if I describe my methodology things will get clearer.

Right after booting each distro I simply open the system monitor and select the TAB that shows CPU, Memory, and Network utilization.  I disconnect the network by the way. Then I start opening a short list of applications that do specific tasks, while seeing how the memory utilization and swap file utilization go up, and how the system performs/behaves.  That's basically it.  Nothing more, nothing less.  Rather simple test.

The following is the list of applications I load in strict order after booting each distro:

1) Two terminal windows
2) A browser window (Iceweasel in Debian, Firefox in Ubuntu)
3) OpenOffice - Write (Debian has version Openoffice v2.0.4; Ubuntu 2.4)
4) OpenOffice - Calc
5) OpenOffice - Impress
6) CD burner (Brasero in Ubuntu, the name of the one in Debian I can't  recall right now)
7) Music Player
8 )Movie Player
9) GIMP


Remember this machine has only 256 MB of RAM, and is configured with a swap file of 512 MB.

Now here's the deal.

**DEBIAN:**
Before loading any application the system monitor reports 89.8 MB of RAM used, 0% of swap file used, this is right after booting the system and logging in.  I started loading all the applications listed above one by one.  Each one loaded rather quickly.  Just left each app open in its own just-started state, with its blank document or whatever it showed, then minimized its window and left it there, open but in the bottom panel.  Debian opened all these nine applications with no problem at all, and showing no noticeable slow down.

After opening and then minimizing GIMP, the nine applications where then loaded in memory.  Memory utilization had jumped up from the initial ~90 MB to  to 157.5 MB in RAM; the amount of SWAP used was only 11 MB.  The mouse showed absolutely no slow down whatsoever in all the process, it was as fast as ever.  Same as the drop down menus from the top panel.  Everything absolutely smooth, with these nine applications open and that memory utilization.  Clicking between the open applications switched to their respective windows basically instantly, with no delay.


**Now UBUNTU:**
Before loading any application the system monitor reports 117 MB of RAM used, 0% of swap file used, this is right after booting Ubuntu and logging in.  I started loading the applications.  First the two terminals, then Firefox (which I now, is heavier than Iceweasel, but remember the purpose of my comparison.)  Then started Openoffice-Write (which I now, v2.4 is heavier than Debian's v2.0, but see comment in my previous parentheses :-))

Now it took OpenOffice-Write a noticeably long time to finally open.  But it did open.  Then I minimized its window and started Calc.  Here the time took even longer, and the mouse started to get jerky.  Then minimized Calc, and invoked OpenOffice-Impress, and it took a seriously loooooong time, and while waiting, I noticed the mouse had already started to break quite too heavily and annoyingly, jumping and not catching up with even very slow hand moves.

And that's all I got.  Then I tried to load application #6, the CD burner, which in Ubuntu corresponds to Brasero, and it never opened.  I waited for about 10 minutes, the mouse had gone down to a miserable crawl, it became quite difficult to do anything with it, because clicks took way to long to respond, same as moves, and location didn't match your click expectations.  I checked memory utilization before quiting:  197.6 MB of the 256 RAM. **Surprisingly ** (at least to me,) **swap file utilization was 0% !!!!! (???) ** CPU utilization, by the way, wasn't anywhere close to 100%, it was varying between ~10 and 25%.  Took note of all this, then clicked on the top panel's  exit button but even after two minutes the logout/reboot/shutdown dialog never came up, so I eventually pressed Ctrl-Alt-Backspace to reinitiate X, and then rebooted into Ubuntu.

I tried a second time.  Doing exactly the same.  All was exactly the same up to OpenOffice impress.  Same loooong times for all the openoffice applications to load, each one slower to load than the previous one.  But I got slightly luckier this time, because Brasero (#6) also took a long time to load, but it did load eventually.  And so did #7 (Rhythmbox), and #8 (Totem).  Mouse was the same as the first time: slowed down to a jerky and incredibly annoying jumpy crawl.  The machine at this stage was way past unuseable, but I wanted to see if it Ubuntu could manage to load the 9 applications, and how the memory did.

After Totem finally loaded, memory used was 196,4MB, but **surprisingly again, swap file utilization was still ZERO!  Then why did Ubuntu get so incredibly low?????**  This puzzles me.  Then when the mouse gave me the chance, I finally invoked GIMP, and after about 5 minutes I wasn't patient enough to wait and see if it would load some time in the future.  The machine was already quite seriously semi-halted and unusable.  With that, I declared completed my humble app loading test and comparison between Ubuntu and Debian, in a low-end, 256 RAM laptop.


This simple comparison makes me wonder if there is a serious memory management bug in Ubuntu 8.04.  One thing is to expect Ubuntu to struggle more than Debian because of loading heavier applications within the same amount of RAM, but another very different thing is to start to be short on RAM and still simply ignore and apparently not use at all the swap file, and yet get the machine and the OS so incredibly slow. Any thoughts on this are more than welcome.


I'm planning to do this exact same test having separate /home partitions for these same two distros, and will also do exactly the same test installing on that same laptop several other distros, both major "heavy" ones like openSUSE, Mandriva, and Fedora, as well and light ones, like DSL, Puppy, Vector, and Slax.  Will create comparison tables to document all the findings I come across, and will post them eventually.

Comments, critiques, observations and recommendations are welcome.  Thanks for reading (if you managed to read the whole thing! :))

-raul

---

### Post by rsaavedra on 2008-07-04
Had a chance to reformat the whole hard drive of this laptop, created partitions similar to the previous time, installed Debian and also Ubuntu once again, both using the same swap space as before.

This second time Ubuntu does run ok on this machine, somewhat similar to Debian, maybe a little slower but not much.  I was able to open the nine applications in my test, mouse was perfectly usable, swap file utilization was non-zero, and switching between applications was relatively fast, maybe not as fast as with Debian, but rather similar, nothing compared to the halting of the machine and the mouse that I experienced the first time with Ubuntu.

So this second time I can't replicate at all the problems I reported in my previous post.  Can't tell what the problem was then though, since the hard drive had also been just formatted the previous time.  And on both ocassions I had downloaded and installed all the Ubuntu updates.

All the other distros face-off still pending, will post about it when I get a chance to do the comparisons.

---

