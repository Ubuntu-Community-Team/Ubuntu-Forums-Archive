---
title: "bug with julius 4.5.x"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by bejimed on 2010-07-22
ihave the ubuntu 10.04 as an Operating sytstem 
and i have installed the julius 4.1.x with the command apt-get install julius 
when i want toconvert the two files x.grammar and x.voca to x.dfa,x.term and x.dict using the command mkdfa.perl i has this error 
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

### Post by bejimed on 2010-07-23
where our answers please it's so urgent

---

### Post by bejimed on 2010-07-26
Help me please

---

