---
title: "make error"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by smss on 2011-10-20
Hello.
When i make the rcssserver-15.0.0 (robocup socccer simulation server),faced to this error:
```
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT coach_lang_tok.lo -MD -MP -MF .deps/coach_lang_tok.Tpo -c -o coach_lang_tok.lo coach_lang_tok.cpp
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT bodysender.o -MD -MP -MF .deps/bodysender.Tpo -c -o bodysender.o bodysender.cpp
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT coach.o -MD -MP -MF .deps/coach.Tpo -c -o coach.o coach.cpp
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT csvsaver.o -MD -MP -MF .deps/csvsaver.Tpo -c -o csvsaver.o csvsaver.cpp
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT dispsender.o -MD -MP -MF .deps/dispsender.Tpo -c -o dispsender.o dispsender.cpp
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT field.o -MD -MP -MF .deps/field.Tpo -c -o field.o field.cpp
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT fullstatesender.o -MD -MP -MF .deps/fullstatesender.Tpo -c -o fullstatesender.o fullstatesender.cpp
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT heteroplayer.o -MD -MP -MF .deps/heteroplayer.Tpo -c -o heteroplayer.o heteroplayer.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I.. -I.. -I/usr/include -W -Wall -g -O2 -MT coach_lang_tok.lo -MD -MP -MF .deps/coach_lang_tok.Tpo -c coach_lang_tok.cpp  -fPIC -DPIC -o .libs/coach_lang_tok.o
coach_lang_tok.cpp:163:8: warning: "/*" within comment
coach_lang_tok.cpp:6658:1: warning: "/*" within comment
coach_lang_tok.cpp:6668:0: warning: "YY_NUM_RULES" redefined
coach_lang_tok.cpp:3942:0: note: this is the location of the previous definition
coach_lang_tok.cpp:6669:0: warning: "YY_END_OF_BUFFER" redefined
coach_lang_tok.cpp:3943:0: note: this is the location of the previous definition
coach_lang_tok.cpp:156:0: error: unterminated #ifndef
coach_lang_tok.cpp: In member function ‘virtual int RCSSPComLexer::yylex()’:
coach_lang_tok.cpp:4177:29: error: ‘YY_BUF_SIZE’ was not declared in this scope
coach_lang_tok.cpp: In member function ‘virtual void RCSSPComFlexLexer::switch_streams(std::istream*, std::ostream*)’:
coach_lang_tok.cpp:4693:50: error: ‘YY_BUF_SIZE’ was not declared in this scope
coach_lang_tok.cpp: In member function ‘virtual void RCSSPComFlexLexer::yyrestart(std::istream*)’:
coach_lang_tok.cpp:5041:37: error: ‘YY_BUF_SIZE’ was not declared in this scope
coach_lang_tok.cpp: At global scope:
coach_lang_tok.cpp:6672:8: error: redefinition of ‘struct yy_trans_info’
coach_lang_tok.cpp:3947:2: error: previous definition of ‘struct yy_trans_info’
coach_lang_tok.cpp:6677:42: error: conflicting declaration ‘const flex_int16_t yy_accept [334]’
coach_lang_tok.cpp:3951:42: error: ‘yy_accept’ has a previous declaration as ‘const flex_int16_t yy_accept [208]’
coach_lang_tok.cpp:6718:46: error: conflicting declaration ‘const yy_state_type yy_NUL_trans [334]’
coach_lang_tok.cpp:3978:46: error: ‘yy_NUL_trans’ has a previous declaration as ‘const yy_state_type yy_NUL_trans [208]’
coach_lang_tok.cpp:6355:1: error: redefinition of ‘int RCSSPComLexer::yylex()’
coach_lang_tok.cpp:4146:1: error: ‘virtual int RCSSPComLexer::yylex()’ previously defined here
coach_lang_tok.cpp:7135:1: error: redefinition of ‘RCSSPComFlexLexer::RCSSPComFlexLexer(std::istream*, std::ostream*)’
coach_lang_tok.cpp:4648:1: error: ‘RCSSPComFlexLexer::RCSSPComFlexLexer(std::istream*, std::ostream*)’ previously defined here
coach_lang_tok.cpp:7165:1: error: redefinition of ‘RCSSPComFlexLexer::~RCSSPComFlexLexer()’
coach_lang_tok.cpp:4678:1: error: ‘virtual RCSSPComFlexLexer::~RCSSPComFlexLexer()’ previously defined here
coach_lang_tok.cpp:7175:6: error: redefinition of ‘void RCSSPComFlexLexer::switch_streams(std::istream*, std::ostream*)’
coach_lang_tok.cpp:4688:6: error: ‘virtual void RCSSPComFlexLexer::switch_streams(std::istream*, std::ostream*)’ previously defined here
coach_lang_tok.cpp:7190:5: error: redefinition of ‘int RCSSPComFlexLexer::LexerInput(char*, int)’
coach_lang_tok.cpp:4703:5: error: ‘virtual int RCSSPComFlexLexer::LexerInput(char*, int)’ previously defined here
coach_lang_tok.cpp:7217:6: error: redefinition of ‘void RCSSPComFlexLexer::LexerOutput(const char*, int)’
coach_lang_tok.cpp:4730:6: error: ‘virtual void RCSSPComFlexLexer::LexerOutput(const char*, int)’ previously defined here
coach_lang_tok.cpp:7229:5: error: redefinition of ‘int RCSSPComFlexLexer::yy_get_next_buffer()’
coach_lang_tok.cpp:4742:5: error: ‘int RCSSPComFlexLexer::yy_get_next_buffer()’ previously defined here
coach_lang_tok.cpp:7363:19: error: redefinition of ‘yy_state_type RCSSPComFlexLexer::yy_get_previous_state()’
coach_lang_tok.cpp:4876:19: error: ‘yy_state_type RCSSPComFlexLexer::yy_get_previous_state()’ previously defined here
coach_lang_tok.cpp:7393:19: error: redefinition of ‘yy_state_type RCSSPComFlexLexer::yy_try_NUL_trans(yy_state_type)’
coach_lang_tok.cpp:4906:19: error: ‘yy_state_type RCSSPComFlexLexer::yy_try_NUL_trans(yy_state_type)’ previously defined here
coach_lang_tok.cpp:7413:10: error: redefinition of ‘void RCSSPComFlexLexer::yyunput(int, char*)’
coach_lang_tok.cpp:4926:10: error: ‘void RCSSPComFlexLexer::yyunput(int, char*)’ previously defined here
coach_lang_tok.cpp:7450:9: error: redefinition of ‘int RCSSPComFlexLexer::yyinput()’
coach_lang_tok.cpp:4963:9: error: ‘int RCSSPComFlexLexer::yyinput()’ previously defined here
coach_lang_tok.cpp:7522:10: error: redefinition of ‘void RCSSPComFlexLexer::yyrestart(std::istream*)’
coach_lang_tok.cpp:5035:10: error: ‘virtual void RCSSPComFlexLexer::yyrestart(std::istream*)’ previously defined here
coach_lang_tok.cpp: In member function ‘virtual yy_buffer_state* RCSSPComFlexLexer::yy_create_buffer(std::istream*, int)’:
coach_lang_tok.cpp:7588:82: error: ‘RCSSCLangFlexLexeralloc’ was not declared in this scope
coach_lang_tok.cpp: In member function ‘virtual void RCSSPComFlexLexer::yy_delete_buffer(yy_buffer_state*)’:
coach_lang_tok.cpp:7622:49: error: ‘RCSSCLangFlexLexerfree’ was not declared in this scope
coach_lang_tok.cpp:7624:37: error: ‘RCSSCLangFlexLexerfree’ was not declared in this scope
coach_lang_tok.cpp: In member function ‘void RCSSPComFlexLexer::yyensure_buffer_stack()’:
coach_lang_tok.cpp:7751:9: error: ‘RCSSCLangFlexLexeralloc’ was not declared in this scope
coach_lang_tok.cpp:7771:9: error: ‘RCSSCLangFlexLexerrealloc’ was not declared in this scope
coach_lang_tok.cpp: In member function ‘void RCSSPComFlexLexer::yy_push_state(int)’:
coach_lang_tok.cpp:7791:65: error: ‘RCSSCLangFlexLexeralloc’ was not declared in this scope
coach_lang_tok.cpp:7794:93: error: ‘RCSSCLangFlexLexerrealloc’ was not declared in this scope
make[3]: *** [coach_lang_tok.lo] Error 1
make[3]: *** Waiting for unfinished jobs....
mv -f .deps/field.Tpo .deps/field.Po
mv -f .deps/heteroplayer.Tpo .deps/heteroplayer.Po
coach.cpp:762:1: warning: unused parameter ‘level’
mv -f .deps/fullstatesender.Tpo .deps/fullstatesender.Po
mv -f .deps/csvsaver.Tpo .deps/csvsaver.Po
mv -f .deps/bodysender.Tpo .deps/bodysender.Po
mv -f .deps/dispsender.Tpo .deps/dispsender.Po
mv -f .deps/coach.Tpo .deps/coach.Po

```Thank you.

---

### Post by smss on 2011-10-20
I installed the libtool by this command [#sudo apt-get install libtool] and know i feced to this error:
```
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT coach_lang_tok.lo -MD -MP -MF .deps/coach_lang_tok.Tpo -c -o coach_lang_tok.lo coach_lang_tok.cpp
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.cpp
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT monitor.o -MD -MP -MF .deps/monitor.Tpo -c -o monitor.o monitor.cpp
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT netif.o -MD -MP -MF .deps/netif.Tpo -c -o netif.o netif.cpp
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT pcombuilder.o -MD -MP -MF .deps/pcombuilder.Tpo -c -o pcombuilder.o pcombuilder.cpp
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT pcomparser.o -MD -MP -MF .deps/pcomparser.Tpo -c -o pcomparser.o pcomparser.cpp
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT player.o -MD -MP -MF .deps/player.Tpo -c -o player.o player.cpp
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT playerparam.o -MD -MP -MF .deps/playerparam.Tpo -c -o playerparam.o playerparam.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I.. -I.. -I/usr/include -W -Wall -g -O2 -MT coach_lang_tok.lo -MD -MP -MF .deps/coach_lang_tok.Tpo -c coach_lang_tok.cpp  -fPIC -DPIC -o .libs/coach_lang_tok.o
coach_lang_tok.cpp:6113:5: error: too many initializers for ‘const flex_int16_t [128]’
coach_lang_tok.cpp:6355:1: error: ‘RCSSPComLexer’ has not been declared
coach_lang_tok.cpp: In function ‘int yylex()’:
coach_lang_tok.cpp:6366:9: error: ‘yy_init’ was not declared in this scope
coach_lang_tok.cpp:6374:11: error: ‘yy_start’ was not declared in this scope
coach_lang_tok.cpp:6377:10: error: ‘yyin’ was not declared in this scope
coach_lang_tok.cpp:6380:10: error: ‘yyout’ was not declared in this scope
coach_lang_tok.cpp:6383:10: error: ‘yy_buffer_stack’ was not declared in this scope
coach_lang_tok.cpp:6383:10: error: ‘yy_buffer_stack_top’ was not declared in this scope
coach_lang_tok.cpp:6384:27: error: ‘yyensure_buffer_stack’ was not declared in this scope
coach_lang_tok.cpp:6386:23: error: ‘yyin’ was not declared in this scope
coach_lang_tok.cpp:6386:41: error: ‘yy_create_buffer’ was not declared in this scope
coach_lang_tok.cpp:6389:26: error: ‘yy_load_buffer_state’ was not declared in this scope
coach_lang_tok.cpp:6394:12: error: ‘yy_c_buf_p’ was not declared in this scope
coach_lang_tok.cpp:6397:13: error: ‘yy_hold_char’ was not declared in this scope
coach_lang_tok.cpp:6404:23: error: ‘yy_start’ was not declared in this scope
coach_lang_tok.cpp:6410:6: error: ‘yy_last_accepting_state’ was not declared in this scope
coach_lang_tok.cpp:6411:6: error: ‘yy_last_accepting_cpos’ was not declared in this scope
coach_lang_tok.cpp:6422:3: error: ‘yytext’ was not declared in this scope
coach_lang_tok.cpp:6431:13: error: ‘yy_last_accepting_cpos’ was not declared in this scope
coach_lang_tok.cpp:6432:24: error: ‘yy_last_accepting_state’ was not declared in this scope
coach_lang_tok.lpp:59:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:60:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:92:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:93:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:94:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:95:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:97:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:98:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:100:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:101:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:114:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:116:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:118:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:120:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:122:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:124:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:126:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:128:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:130:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:132:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:134:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:136:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:138:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:140:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:142:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:144:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:146:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:165:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:166:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:174:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:176:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:178:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:180:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:182:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:184:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:187:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:189:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:191:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:193:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:200:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:201:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:202:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:203:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:205:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:208:4: error: ‘M_lexed_val’ was not declared in this scope
coach_lang_tok.lpp:213:1: error: ‘LexerOutput’ was not declared in this scope
coach_lang_tok.cpp:7013:8: error: ‘yy_buffer_stack’ was not declared in this scope
coach_lang_tok.cpp:7013:8: error: ‘yy_buffer_stack_top’ was not declared in this scope
coach_lang_tok.cpp:7024:5: error: ‘yy_n_chars’ was not declared in this scope
coach_lang_tok.cpp:7025:46: error: ‘yyin’ was not declared in this scope
coach_lang_tok.cpp:7036:25: error: ‘yy_buffer_stack’ was not declared in this scope
coach_lang_tok.cpp:7036:25: error: ‘yy_buffer_stack_top’ was not declared in this scope
coach_lang_tok.cpp:7036:62: error: ‘yy_n_chars’ was not declared in this scope
coach_lang_tok.cpp:7042:47: error: ‘yy_get_previous_state’ was not declared in this scope
coach_lang_tok.cpp:7053:55: error: ‘yy_try_NUL_trans’ was not declared in this scope
coach_lang_tok.cpp:7072:38: error: ‘yy_get_next_buffer’ was not declared in this scope
coach_lang_tok.cpp:7076:6: error: ‘yy_did_buffer_switch_on_eof’ was not declared in this scope
coach_lang_tok.cpp:7078:19: error: ‘yywrap’ was not declared in this scope
coach_lang_tok.cpp:7098:7: error: ‘yyin’ was not declared in this scope
coach_lang_tok.cpp:7098:7: error: ‘yyrestart’ was not declared in this scope
coach_lang_tok.cpp:7107:48: error: ‘yy_get_previous_state’ was not declared in this scope
coach_lang_tok.cpp:7127:3: error: ‘LexerError’ was not declared in this scope
coach_lang_tok.cpp: In destructor ‘virtual RCSSCLangFLexLexer::~RCSSCLangFLexLexer()’:
coach_lang_tok.cpp:7168:41: error: ‘RCSSCLangFlexLexerfree’ was not declared in this scope
coach_lang_tok.cpp: In member function ‘int RCSSCLangFLexLexer::yy_get_next_buffer()’:
coach_lang_tok.cpp:7298:74: error: ‘RCSSCLangFlexLexerrealloc’ was not declared in this scope
coach_lang_tok.cpp:7347:131: error: ‘RCSSCLangFlexLexerrealloc’ was not declared in this scope
coach_lang_tok.cpp: In member function ‘virtual yy_buffer_state* RCSSCLangFLexLexer::yy_create_buffer(std::istream*, int)’:
coach_lang_tok.cpp:7588:82: error: ‘RCSSCLangFlexLexeralloc’ was not declared in this scope
coach_lang_tok.cpp: In member function ‘virtual void RCSSCLangFLexLexer::yy_delete_buffer(yy_buffer_state*)’:
coach_lang_tok.cpp:7622:49: error: ‘RCSSCLangFlexLexerfree’ was not declared in this scope
coach_lang_tok.cpp:7624:37: error: ‘RCSSCLangFlexLexerfree’ was not declared in this scope
coach_lang_tok.cpp: In member function ‘void RCSSCLangFLexLexer::yyensure_buffer_stack()’:
coach_lang_tok.cpp:7751:9: error: ‘RCSSCLangFlexLexeralloc’ was not declared in this scope
coach_lang_tok.cpp:7771:9: error: ‘RCSSCLangFlexLexerrealloc’ was not declared in this scope
coach_lang_tok.cpp: In member function ‘void RCSSCLangFLexLexer::yy_push_state(int)’:
coach_lang_tok.cpp:7791:65: error: ‘RCSSCLangFlexLexeralloc’ was not declared in this scope
coach_lang_tok.cpp:7794:93: error: ‘RCSSCLangFlexLexerrealloc’ was not declared in this scope
make[3]: *** [coach_lang_tok.lo] Error 1
make[3]: *** Waiting for unfinished jobs....
mv -f .deps/pcombuilder.Tpo .deps/pcombuilder.Po
mv -f .deps/pcomparser.Tpo .deps/pcomparser.Po
player.cpp:1701:1: warning: unused parameter ‘level’
mv -f .deps/main.Tpo .deps/main.Po
mv -f .deps/netif.Tpo .deps/netif.Po
mv -f .deps/monitor.Tpo .deps/monitor.Po
mv -f .deps/playerparam.Tpo .deps/playerparam.Po
mv -f .deps/player.Tpo .deps/player.Po

```

---

