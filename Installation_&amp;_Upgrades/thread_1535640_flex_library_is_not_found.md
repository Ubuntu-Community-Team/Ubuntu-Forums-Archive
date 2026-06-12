---
title: "flex library is not found"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by bejimed on 2010-07-21
iwant to install julius 3.5.2 on my system but i have an error after compiling the file configure 
the error is 
flex library is not found 
so what i have to do thanks

---

### Post by lykeion on 2010-07-21
Julius 4.1.2 is in the repos, install with:
```
sudo apt-get install julius
```

---

### Post by bejimed on 2010-07-28
thank you my friend for your advice but i have another problem i use the script mkdfa.pl in order to convert  the two files x.grammar and x.voca to x.dfa,x.term and x.dict using the command mkdfa.perl i has this error 
$ ./mkdfa.pl sample 
sample.grammar has 3 rules
sample.voca    has 6 categories and 18 words
---
Now parsing grammar file
Now modifying grammar to minimize states[-1]
Now parsing vocabulary file
Now making nondeterministic finite automaton[3/3]
Error:       undefined class "DIG"
---
no .dfa or .dict file generated

NB : mkfa and dfa_minimize internally are  placed at the same directory as mkdfa.pl. 
so please help me

---

### Post by lykeion on 2010-07-30
hi again
two things:
1) when a problem has been solved please tag this thread as SOLVED
2) instead of appending further questions on a week old thread, it's better to create a new thread

about your question on how to use mkdfa.pl, you can't expect everyone to know what this is, so please add some links or explanations on what you talk about

because I am such a helpful soul I googled it and found out it is a part of gramtools which is part of the voxforge project

since this is very specific I'd suggest you use the **_[Julius Forum]("http://julius.sourceforge.jp/forum/")_** instead of this forum (maybe I'm wrong but my guess is that this thread won't get any more posts)

---

