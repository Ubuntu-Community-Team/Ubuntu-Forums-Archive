---
title: "Problems in Terminal after update"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by ramdisk on 2006-10-28
I have been using dapper for a while on several computers.  I reinstalled from scratch to edgy on one last night.  When I go to the terminal and get into vi I am noticing some differences.  In dapper when I hit the insert key, it lights up with "insert" in red at the bottom of the vi screen.  does not do so in edgy.  When I use the arrow keys in insert mode in vi in dapper works fine. In edgy I get the letters A B C D when I try to use arrow keys.  Any idea what the problem could be?  Tried googleling and searching the forums but have hit my wits end for a saturday morning! was hoping someone else had a solution .. Thanx for you time

ramdisk

---

### Post by ethan@xmlstandards.org on 2006-10-28
I have encountered exactly the same issues when using vi via terminal.

Not sure what is going on either.

Back to Dapper for me I fear. Shame too!

---

### Post by meimato on 2006-10-30
Same problem for me. I even tried with aterm, but the problem is the same.
Moreover, vi has strange behaviours also using it from a console (tty1, tty2...).
Someone has an idea to solve this problem?

---

### Post by meimato on 2006-10-30
I found that using the command vim instead of vi solves the problem.

---

### Post by jeblinux on 2006-11-02
You can use the 'which' command to track down what command is being executed when you type 'vi'. Then you can use 'readlink' to find the target of the symbolic links. In one step this could be

$ readlink -f $(which vi)

which indicates to me that using vi or vim makes no difference on my system---they both point to '/usr/bin/vim.basic'. I just upgraded from Dapper Drake to Edgy Eft a few days ago.

It sounds like you are in vi-compatible mode. This will likely be the default behavior if you do not have a ~/.vimrc file to change it otherwise. or some other system configuration file. On my system the file '/etc/vim/vimrc' sources the file '/usr/share/vim/vim70/debian.vim' to setup the most basic stuff. I put more advanced/personal options in my '~/.vimrc' file.

I tried it on my computer to see if compatible mode gave the behavior you described. If I start vi and then type the command ':set compatible' then everything weird happens like you describe. Just create a file called '.vimrc' in your home directory and enter the line

set nocompatible

in that file. You may want other options such as

syntax on

that make vim less like vi but more useful.

If you don't want to make your own there are several good ones that you can grab off the Net.

---

### Post by kr4z on 2006-11-17
The problem seems to happen because on edgy, vim-tiny is installed by default instead of vim-full. This means that vim uses the /etc/vim/vimrc.tiny file instead of the /etc/vim/vimrc file. The vimrc file sets nocompatible mode, while vimrc.tiny does not.

There's a bug about this here:
[https://launchpad.net/distros/ubuntu/+source/vim/+bug/72174](https://launchpad.net/distros/ubuntu/+source/vim/+bug/72174)

You can get the old behavior back by installing the vim-full package.

---

