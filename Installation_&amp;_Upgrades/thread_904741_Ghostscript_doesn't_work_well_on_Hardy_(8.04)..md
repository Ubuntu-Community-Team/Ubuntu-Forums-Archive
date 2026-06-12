---
title: "Ghostscript doesn't work well on Hardy (8.04)."
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by chenjin824 on 2008-08-29
Hi all,

The problem is that the installation seems fine but when i 
tried to use ps2pdf tool to convert ps file to a pdf file, it failed reporting:

Error: /invalidfont in /findfont
Operand stack:
   Fa   140   --nostringval--   26   3   --nostringval--   33   33   4   --nostringval--   18   3   --nostringval--   29   17   --nostringval--   33   9   --nostringval--   22   73   --nostringval--   --nostringval--   7   66.4176   Times-Italic
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1889   1   3   %oparray_pop   1888   1   3   %oparray_pop   1872   1   3   %oparray_pop   1755   1   3   %oparray_pop   --nostringval--   %errorexec_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   1847   26   4   %oparray_pop
Dictionary stack:
   --dict:1148/1684(ro)(G)--   --dict:0/20(G)--   --dict:94/200(L)--   --dict:99/300(L)--
Current allocation mode is local
Last OS error: 2
Current file position is 24573
GPL Ghostscript SVN PRE-RELEASE 8.61: Unrecoverable error, exit code 1

It happened to all the ps file, so it's definitely not the source file problem. Actually gphostscript on Fedora Core 8 works as a charm. 

Does anybody succeed in using this ghostscript in Ubuntu Hardy?
I'm afraid it is an unbelievable bug in Ubuntu?

Jin

---

