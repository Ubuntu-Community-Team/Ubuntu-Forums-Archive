---
title: "vim and ruby within Natty 11.04"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by Ricalsin on 2011-05-12
Has anyone else noticed that you cannot get ruby to work in vim on the new Natty 11.04?  No vim-ruby in Natty.  Vim 7.3 states it needs ruby1.9.1-dev but even that is not getting the "+ruby" in a "vim --version" command after compiling the binaries.  This problem stops some significant vim scripts from working.  

I have exhausted myself and cannot find an answer.  I think the problem is somewhere in the vim version released by Natty (vim-7.3.035) and the latest vim release on the mercurial site.  When I used the very latest release of vim (vim-7.3.277) from Mercurial, I WAS able to get the "vim --version" = "+ruby"  But that version of vim did not work within Natty, showing a significant error after running "make test" about not being able to locate an object or something (sorry, didn't write it down) - couldn't even get a file to load when running that version of vim.  So it loaded the ruby code but then had other problems.  Going back to the vim version that was released within Natty (vim-7.3.035) still produced no +ruby in a "vim --version" command though it can open a file and read it.  

Yes, I'm doing the obvious; changing the Makefile "--enable-rubyinterp",  doing a "make uninstall" a "make clean" and a "make install".  Still no success.  I'm dreary and a bit pissed that Ubuntu seems to have missed this (significant) error.  But I would be happy to know I missed something simple.

Any thoughts?  (Thanks.)

Rick

---

### Post by Ricalsin on 2011-05-14
<bump>

---

### Post by fooblah on 2011-06-15
I figured this out.  The solution is strange.

First, of course fuzzy_file_finder gem must be installed.

Then you'll need to make two edits to ~/.vim/plugins/fuzzyfinder_textmate.vim


**_First_**: To fix this error:
```
Error detected while processing function InstantiateTextMateMode:
line    5:
LoadError: (eval):6:in `require': no such file to load -- fuzzy_file_finder
```
Add
```
require 'fileutils'
```
to line 55 (first ruby line in InstantiateTextMateMode)

**_Then_**: To fix this error when using the plugin:

```
Error detected while processing function <SNR>17_CompleteFunc..212:
line   27:
NoMethodError: private method `split' called for ["."]:Array
```

Change line 100 to
```

roots = VIM.evaluate("g:fuzzy_roots")
roots = roots.split("\n") if roots.respond_to?(:split)

```
from
```

roots = VIM.evaluate("g:fuzzy_roots").split("\n")

```
That function used to return a string but now returns an array.


Don't ask how I figured out #1, just totally random thrashing and it worked.

---

