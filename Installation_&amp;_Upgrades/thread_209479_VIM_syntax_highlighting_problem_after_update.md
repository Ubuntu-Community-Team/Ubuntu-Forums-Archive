---
title: "VIM syntax highlighting problem after update"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by Nickb-k on 2006-07-05
Hello,

After updating Dapper a couple of days ago syntax highlighting in VIM 6.4.6 has not been working.  At first I had the same problem as reported here: [http://www.ubuntuforums.org/showthread.php?t=161862](http://www.ubuntuforums.org/showthread.php?t=161862)

I followed the instructions and that problem has stopped, but I still have to highlighting.  I've tried:

```
:syntax on
``` from within VIM.

I have uncommented the syntax on lines in my vimrc file, which looks like this:

```
" Configuration file for vim
set runtimepath=~/.vim,/usr/share/vim/addons,/usr/share/vim/vimfiles,/usr/share/vim/vimcurrent,/usr/share/vim/vimfiles/after,/usr/share/vim/addons/after,~/.vim/after,/usr/share/vim/vim64

" Normally we use vim-extensions. If you want true vi-compatibility
" remove change the following statements
set nocompatible        " Use Vim defaults instead of 100% vi compatibility
set backspace=indent,eol,start  " more powerful backspacing

" Now we set some defaults for the editor
" set autoindent                " always set autoindenting on
" set linebreak         " Don't wrap words by default
set textwidth=0         " Don't wrap lines by default
set nobackup            " Don't keep a backup file
set viminfo='20,\"50    " read/write a .viminfo file, don't store more than
                        " 50 lines of registers
set history=50          " keep 50 lines of command line history
set ruler               " show the cursor position all the time

" Suffixes that get lower priority when doing tab completion for filenames.
" These are files we are not likely to want to edit or read.
set suffixes=.bak,~,.swp,.o,.info,.aux,.log,.dvi,.bbl,.blg,.brf,.cb,.ind,.idx,.ilg,.inx,.out,.toc

" We know xterm-debian is a color terminal
if &term =~ "xterm-debian" || &term =~ "xterm-xfree86"
  set t_Co=16
  set t_Sf=^[[3%dm
  set t_Sb=^[[4%dm
endif

" Vim5 and later versions support syntax highlighting. Uncommenting the next
" line enables syntax highlighting by default.
 syntax on

" If using a dark background within the editing area and syntax highlighting
" turn on this option as well
 set background=dark

if has("autocmd")
 " Enabled file type detection
 " Use the default filetype settings. If you also want to load indent files
 " to automatically do language-dependent indenting add 'indent' as well.
 filetype plugin on

endif " has ("autocmd")

" Some Debian-specific things
if has("autocmd")
  augroup filetype
    au BufRead reportbug.*              set ft=mail
   au BufRead reportbug-*              set ft=mail
  augroup END
endif

" Set paper size from /etc/papersize if available (Debian-specific)
if filereadable("/etc/papersize")
  try
    let s:shellbak = &shell
    let &shell="/bin/sh"
    let s:papersize = matchstr(system("cat /etc/papersize"), "\\p*")
    let &shell=s:shellbak
    if strlen(s:papersize)
      let &printoptions = "paper:" . s:papersize
    endif
  catch /^Vim\%((\a\+)\)\=:E145/
  endtry
endif

" The following are commented out as they cause vim to behave a lot
" different from regular vi. They are highly recommended though.
"set showcmd            " Show (partial) command in status line.
"set showmatch          " Show matching brackets.
"set ignorecase         " Do case insensitive matching
"set incsearch          " Incremental search
"set autowrite          " Automatically save before commands like :next and :make

" Source a global configuration file if available
if filereadable("/etc/vim/vimrc.local")
  source /etc/vim/vimrc.local
endif

```

I've checked the /usr/share/vim/vim64/syntax file and I have the relevant .vim files for the language I'm using.

I thought that maybe updating to VIM 7.0 would help, but I'm not really up for compiling from source.  Can anyone suggest anything that I haven't thought of?

Thanks for the help in advance,

Nick

---

### Post by jtwJGuevara on 2006-09-03
I'm probably too late in posting this, but I also did the following while in VIM

```
:syntax enable
```

---

