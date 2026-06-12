---
title: "Vim Ctrl Mappings all wierd"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by omyar on 2007-07-14
Hi folks. This will be my first post. 

I've been having this issue for a while now, and just can't find the answer, I think it might be very rare. Anyhow.

As far as I can remember it started after upgrading to Feisty. Basically, I use Ctrl and the arrow keys for navigation, and it ain't workin. Whenever I press Ctrl-Left, it prints out the string "1;5D" on a new line. 

Ctrl-Right gives me 1;5C
Ctrl-Up gives          1;5A
Ctrl-Down gives    1;5B

and so on.

I have Vim set up as my main programming environment, and have switched to using a Thinkpad x60 roughtly around the same time as I upgraded. 

I tried tried playing with the keyboard settings, but no joy. And have been trawling through the vim homepage looking for the right mapping code.

I'd have to assume at this point that it's more to do with the keyboard sending a different signal for Ctrl-Whatever than vim is used to, but can't figure out how to fix it.

Anyways, thanks for any help in advance

Ray

My .vimrc looks like
syn on
set autoindent
nnoremap <C-Right> w
nnoremap <C-Left> b
inoremap <C-Right> w
inoremap <C-Left> b
set title
set tabstop=4
set ruler
set mouse=a
map <f2> <esc>:VSTreeExplore<return>
set expandtab
set guifont=Bitstream\ Vera\ Sans\ Mono\ 8
set ignorecase
set hlsearch
map <C-t> <ESC>:tabnew<cr>
nnoremap <C-S-Left> <ESC>:tabp<cr>
nnoremap <C-S-Right> <ESC>:tabn<cr>
map <C-H> <ESC>:tabp<cr>
map <C-L> <ESC>:tabn<cr>
map <C-w> <ESC>:tabclose<cr>
set bs=2
set background=dark

---

