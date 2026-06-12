---
title: "filenames ending with whitespace character"
date: 2024-07-07
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2024-07-07
is it _allowed_ for any file being installed by any package in the Ubuntu repository to end with any whitespace character, especially the space character (ASCII 32)? _allowed_, as in a policy not to distribute a package that installs such files.

the purpose for knowing is to correctly parse the lists of file paths found in [FONT=courier new]/var/lib/apt/lists/*.lz4[/FONT] after decompression.  parsing these lists requires know the length of each path.  that length cannot be determined if the name ends in a space character due to a varying number of spaces following some paths in these lists.  a name ending in a space character would be very unusual but is not impossible in the usual file systems seen in Linux or Unix.  depending on how parsing code is written, other whitespace characters could also affect the parsing.

---

### Post by currentshaft on 2024-07-07
I can't answer the first question, but there are likely better ways to parse file listings than deliminating on a whitespace character.

You should post the code and what problem it is meant to solve for an improved solution.

---

### Post by Skaperen on 2024-07-07
there is no code, yet.  the problem was mostly described.  it is to make a database that i can use a file name or path, or part of one to find the full path it could be and what package it could be in.  these lists files that are lz4 compressed (bz2 would make them about half size and thus faster to download, especially on a sub-broadband connection) contain lists of paths with the path in column 1 and the package name in column 2.  between the columns are one or more space characters.  so a path can be followed by a variable number of spaces.

---

### Post by Impavidus on 2024-07-07
Like in the dpkg --search command or the web interface at packages.ubuntu.com, right? I've never seen a file name in a package ending in whitespace, but I don't know whether this is official policy.

---

### Post by TheFu on 2024-07-07
You can name files anything you like on Unix systems with Unix/Linux file systems.  Typically, filenames with extra spaces are accidental and a mistake.  If they are set on purpose, I would suspect nefarious reasons.

I've never seen an official package name with a space in it either.

---

### Post by currentshaft on 2024-07-07
> **Skaperen said:**
> there is no code, yet.  the problem was mostly described.  it is to make a database that i can use a file name or path, or part of one to find the full path it could be and what package it could be in.  these lists files that are lz4 compressed (bz2 would make them about half size and thus faster to download, especially on a sub-broadband connection) contain lists of paths with the path in column 1 and the package name in column 2.  between the columns are one or more space characters.  so a path can be followed by a variable number of spaces.

Again, files can be listed in a way which do not require you to delimit the output by spaces to parse, for example:

$ touch test1 test\ 2 test3\
$ python
>>> import os
>>> os.listdir(".")
['test3 ', 'test 2', 'test1']

---

### Post by Skaperen on 2024-07-07
> **TheFu said:**
> You can name files anything you like on Unix systems with Unix/Linux file systems.  Typically, filenames with extra spaces are accidental and a mistake.  If they are set on purpose, I would suspect nefarious reasons.

I've never seen an official package name with a space in it either.

actually, many installable files have spaces in the middle of the name.  counting files in directories with a space (because a simple grep over paths could not distinguish if a space follows the last '/' or not) there are over 900,000 possible.  but these are in the middle.  i did not try to check for spaces at the end because of the spaces that are there in the form the files are already in.  those "lz4" (bad choice to compress distributed files) files have path followed by package with multiple spaces between them if the path is quite short (no real need to do this for the purpose of these files).  if a file path really is short and has a space at the end, that space would be followed by the space(s) that follow the path and would look like a shorter path.  long paths would have just one separator and so there would be two spaces (the one at the end of the path and the one that separates the path from the package).

after decompressing those files, try reversing the order of path and package they are in now to be package and path.  it's not so easy (impossible if paths can end with a space in them).

i'd show things but the code tag in this forum still doesn't work right with regard to multiple spaces and text with variable width characters.

---

### Post by Skaperen on 2024-07-07
> **currentshaft said:**
> Again, files can be listed in a way which do not require you to delimit the output by spaces to parse, for example:

$ touch test1 test\ 2 test3\
$ python
>>> import os
>>> os.listdir(".")
['test3 ', 'test 2', 'test1']

try doing that with the existing files:
```

time (cat /var/lib/apt/lists/*.lz4|lz4 -d|wc -lc)

```
the above command will take a while to run, depending on your device speeds, from a few seconds to a few minutes.  then it will show you the total number of lines and the total number of bytes.  on my 20.04 (focal fossa) system i got 140,272,319 lines and 15,526,111,353 bytes in 5 seconds.  fortunately, *lz4* supports concatenating compressed files together.

trying to convert those lists to python lists will need a lot of RAM.  even as tuples it will need a lot.  good luck parsing these files (after decompression) to create a list of 140+ million items containing 15+ billion characters.  you'll need at least a 32GB machine.  have fun!

---

### Post by currentshaft on 2024-07-07
> **Skaperen said:**
> try doing that with the existing files:
```

time (cat /var/lib/apt/lists/*.lz4|lz4 -d|wc -lc)

```
the above command will take a while to run, depending on your device speeds, from a few seconds to a few minutes.  then it will show you the total number of lines and the total number of bytes.  on my 20.04 (focal fossa) system i got 140,272,319 lines and 15,526,111,353 bytes in 5 seconds.  fortunately, *lz4* supports concatenating compressed files together.

trying to convert those lists to python lists will need a lot of RAM.  even as tuples it will need a lot.  good luck parsing these files (after decompression) to create a list of 140+ million items containing 15+ billion characters.  you'll need at least a 32GB machine.  have fun!

I do not have any lz4 files in /var/lib/apt/lists nor have any idea why you're trying to decompress all of them.

Your question is like asking how to fit a circular window without giving any information about the construction of the rest of the house.

Instead of asking to us to guess what you're trying to ultimately do, can you just inform us in an unambiguous way, with examples of input and output in the desired program?

---

### Post by TheFu on 2024-07-08
> **Skaperen said:**
> actually, many installable files have spaces in the middle of the name.  counting files in directories with a space (because a simple grep over paths could not distinguish if a space follows the last '/' or not) there are over 900,000 possible.  but these are in the middle.  i did not try to check for spaces at the end because of the spaces that are there in the form the files are already in.  those "lz4" (bad choice to compress distributed files) files have path followed by package with multiple spaces between them if the path is quite short (no real need to do this for the purpose of these files).  if a file path really is short and has a space at the end, that space would be followed by the space(s) that follow the path and would look like a shorter path.  long paths would have just one separator and so there would be two spaces (the one at the end of the path and the one that separates the path from the package).

after decompressing those files, try reversing the order of path and package they are in now to be package and path.  it's not so easy (impossible if paths can end with a space in them).

i'd show things but the code tag in this forum still doesn't work right with regard to multiple spaces and text with variable width characters.


If the "installable files" have spaces in them, I'd first wonder where you are finding these.  I just searched my APT cache which has all the deb packages for 6 OSes inside it - NONE, ZERO, NADA have spaces in any filenames. NONE.

I can't remember ever seeing official package filenames with spaces inside them.  Additionally, on my systems, I don't allow spaces in file names.  I use a little rename script to fix filenames with spaces, to prevent it.  If you use tab completion, it is pretty clear when a filename has odd characters, like a space, because the entire filename will be quoted automatically.

The worst places I have to deal with spaces in filenames is video or audio content.  As those files arrive, I fix the filenames with the script.  A number of us in these forums have posted our file renaming scripts multiple times.  Mine just uses the perl 'rename' command a few times to replace spaces with '_' characters, then remove duplicates and if there's a '_-_', to change that into a '-'.  Also, since I record OTA TV and those recordings have timestamps in their filenames, my script cleans those up into SxxExx instead by doing some fancy grep/cut from text files holding that information.

Allowing spaces in filenames breaks lots of my scripts, so it is just best for me to prevent them from the start.  It is mostly automatic at this point, unless there are conflicting final names that need manual resolution.

---

### Post by Skaperen on 2024-07-08
> **currentshaft said:**
> I do not have any lz4 files in /var/lib/apt/lists nor have any idea why you're trying to decompress all of them.

Your question is like asking how to fit a circular window without giving any information about the construction of the rest of the house.

Instead of asking to us to guess what you're trying to ultimately do, can you just inform us in an unambiguous way, with examples of input and output in the desired program?

i have assumed these file come with Ubuntu.  maybe they come with some package i have installed even though they do not list any _**[FONT=courier new].lz4[/FONT]**_ files as part of any package.  maybe they have changed to a better compression and now use that new extension.  try (as a non-root user*) this command (especially if you are running 20.04 focal fossa):  _**[FONT=courier new]ls -dl /var/lib/apt/lists/*Contents*[/FONT]**_ (note the capital "C" which can just be left out).

these files, one for each repository and architecture, list files, one per line, with which packages (comma separated) they come in.  the file path is first.  the file path may have embedded spaces. then there is one or more spaces, then the list of packages (i have never seen a space here).  what i am wanting to do is build a better search tool that can show what packages a file comes in and what other files are in the same package.  i also want to build a more compact list that has each package name once followed by each path in that package.  a list of just package names can also be of some help.  if Ubuntu no longer provides these files, my project gets butter and jelly spread over it in the morning.

* never, ever, run _any_ command from _any_ forum as root (or with *sudo* or *su*) unless *you* are an _expert_ in that command.

---

### Post by TheFu on 2024-07-08
Just sayin'
```
$ ls /var/lib/apt/lists/*\ *
ls: cannot access '/var/lib/apt/lists/* *': No such file or directory
```
I don't have any files in that directory with "Contents" in the name anywhere either.  Something specific to your system.  The filenames do have a 1-to-1 connection to the repo they are tied to, at least in my systems they do. There are a few PPAs, but most are core Ubuntu repos.

Also, 
>     * never, ever, run any command from any forum as root (or with sudo or su) unless you are an expert in that command. 
I don't think you need to be an expert, but you should look up what the command does, if you don't know it already AND all the options.

Anyway, we've beat this to death now.

---

### Post by Skaperen on 2024-07-08
> Anyway, we've beat this to death now.

probably so.  i don't think this will be resolved here.  i have ideas for parsing (should be easier in C than in Python) but must assume no spaces are attached at the end of a path even though such a file can be created (i have created one).  the best i can do is create a tool to look at what has been installed to see if there are any "tail spaces".

in any case, here is what my system has.  some of them have been recently updated.  i have been doing full upgrades, recently (almost daily).

```

lt1a/forums/3 /home/forums 6> ls -dl /var/lib/apt/lists/*.lz4
-rw-r--r-- 1 root root 420490558 Jul  4 20:13 /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_focal-security_Contents-amd64.lz4
-rw-r--r-- 1 root root 183646889 Jul  5 03:27 /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_focal-security_Contents-i386.lz4
-rw-r--r-- 1 root root   1360669 May 24  2023 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_focal-backports_Contents-amd64.lz4
-rw-r--r-- 1 root root   1299225 May 24  2023 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_focal-backports_Contents-i386.lz4
-rw-r--r-- 1 root root  68899585 Apr 23  2020 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_focal_Contents-amd64.lz4
-rw-r--r-- 1 root root  53966351 Apr 23  2020 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_focal_Contents-i386.lz4
-rw-r--r-- 1 root root 443463753 Jul  4 21:57 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_focal-updates_Contents-amd64.lz4
-rw-r--r-- 1 root root 195585943 Jul  5 03:45 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_focal-updates_Contents-i386.lz4
lt1a/forums/3 /home/forums 7>

```

---

### Post by Skaperen on 2024-07-08
i found why i have these files.

i have installed and configured a package named *apt-file*.  *apt-file* is a tool that allows listing the contents of a package, even if you have not installed it.  obviously, it needs to have a list somewhere.  you'd think Canonical could host such a tool online, maybe with ads.

*apt-file* causes **_[FONT=courier new]apt-get update[/FONT]_** to download these lists if they need to be updated (some other package renames or adds files).  this explains some slowness i have seen sometimes with _**[FONT=courier new]apt-get update[/FONT]**_.

so, i now have 2 things: [1] develop a parser for these files.  i'll just assume a "tail space" never happens.  i can work around "embedded spaces" (even if many in a row).  [2] contact the developer of *apt-file* to improve the downloading and/or use a better compression instead of *lz4*.  *bz2* works nearly as good as *xz* on these files in terms of file size (almost half) and *bz2* does it a lot faster than *xz* does.

---

### Post by currentshaft on 2024-07-08
I think I understand the problem you described now ...

sudo cat /var/lib/apt/lists/*.lz4|lz4 -d > lz4

I have 18999966 lines in that file.

Let's split on a space and count the number of lines for 1-20 unique elements:

for x in {1..20} ; do printf "%s:" $x ; awk -v c=$x -F " " '{print $c}' lz4 | grep -v "^$" | wc -l ; done
1:18999966
2:18999966
3:31453
4:16698
5:9553
6:6027
7:3400
8:2062
9:1382
10:1036
11:594
12:374
13:224
14:156
15:112
16:80
17:54
18:40
19:22
20:20

Interesting results. I would probably feed the first and second elements into Python to see if the second one looks like it might be part of path in the first element.

Edit:

with open("lz4", "r") as f:
  x = f.read().split("\n")

Removing space elements:

lines = []
for y in x:
  lines.append(' '.join(y.split(" ")).split())

len(lines)
18999967

Checking out the results unfortunately leads to the conclusion there are in fact many spaces in filenames in those files:

for line in lines:
  if len(line) > 2:
    print(line)

Some examples:

['etc/shellinabox/options-available/00+Black', 'on', 'White.css', 'universe/web/shellinabox']
['usr/lib/libreoffice/share/gallery/signs', 'and', 'symbols.thm', 'universe/graphics/openclipart-libreoffice']
['usr/lib/python3/dist-packages/persepolis/Persepolis', 'Download', 'Manager.py', 'universe/net/persepolis']

However, there do not appear to be any spaces in the second element of this list:

for y in x:
  lines.append(y.rsplit(" ", 1))

len(lines)
18999967

for line in lines:
if len(line) > 2:
print(line)
<no results>

for line in lines:
  if "Persepolis Download" in line[0]:
    print(line)
['usr/lib/python3/dist-packages/persepolis/Persepolis Download Manager.py', 'universe/net/persepolis']

Hope that helps. Took about 8 Gb of memory in Python 3.

If you're short on resources, it can be done with awk too, e.g.:

cat lz4 | rev | awk -F" " '{$1=""; print $0}' | rev | grep Persepolis
usr/lib/python3/dist-packages/persepolis/Persepolis Download Manager.py

Just look at all these whitespace characters ...

cat lz4 | rev | awk -F" " '{$1=""; print $0}' | rev | egrep " \w+" | head | sed 's/\^I//g'
etc/shellinabox/options-available/00+Black on White.css
etc/shellinabox/options-available/00_White On Black.css
etc/shellinabox/options-available/01+Color Terminal.css
etc/testssl/DST Root CA X3.txt
lib/firmware/brcm/brcmfmac43241b4-sdio.Intel Corp.-VALLEYVIEW C0 PLATFORM.txt.zst
lib/firmware/brcm/brcmfmac43340-sdio.ASUSTeK COMPUTER INC.-TF103CE.txt.zst
lib/firmware/brcm/brcmfmac43362-sdio.ASUSTeK COMPUTER INC.-ME176C.txt.zst
lib/firmware/brcm/brcmfmac43455-sdio.MINIX-NEO Z83-4.txt.zst
lib/firmware/brcm/brcmfmac4356-pcie.Intel Corporation-CHERRYVIEW D1 PLATFORM.txt.zst
lib/firmware/brcm/brcmfmac4356-pcie.Xiaomi Inc-Mipad2.txt.zst

---

### Post by Skaperen on 2024-07-09
[1] you don't need sudo to read those .lz4 files.  any user can read them.

[2] do you really need that extra _leading space_ in the *awk* string argument you get with _awk -F" " '{whatever}'_?  i've never needed that and i use *awk* often. 

[3] .split() will be a problem in Python.  you could remove the last item from the list.  what remains are the space separated pieces of the file path.  but, what if there are 2 spaces together or a space at the end?  .split(" ") might be better. but for some short paths, there are extra spaces to make the package names line up from one line to the next (no real need to have that).

[4] i am developing a parser in C.  it will parse from the end (the zero byte i put in place of the newline byte.  but, i see that *rev* could have helped.  i didn't think of *rev* (i rarely use it).  it would make the package name be first.  but there is still the multi spaces ambiguity.  i'll see what i get with the parser in C.

[5] so you must have package *apt-list* installed.  what version of Ubuntu are you running?

---

### Post by currentshaft on 2024-07-09
1. This is a throwaway vm, the root boundary is meaningless.

2. The "leading space" after the -F flag to awk tells it to delimit on a space. Is that what you're asking about?

3. I'm not using split, I'm using rsplit. As I had explained, the final element of each line is not space-delimited, so it can be used as an offset for the rest of the fields.

4. I have no idea why you would do this in C, after I have provided you with a solution in Python and Bash. Again, reversing each line ensures you split on the final element which is guaranteed not to have a space.

5. Ubuntu 24 LTS. I installed the package you inquired about. Very interesting problem and I hope you found the replies helpful.

---

