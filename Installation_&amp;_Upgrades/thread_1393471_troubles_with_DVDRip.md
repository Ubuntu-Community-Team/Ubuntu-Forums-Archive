---
title: "troubles with DVDRip"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by SGC622 on 2010-01-29
I installed DVDRip but im having troubles starting the application or is it an add-on? im new to linux still here how i installed it in Terminal (i did not add the script from when i unzipped it )

> 
scott@Home:~/Downloads/dvdrip$ sudo make install                                                                                                                       
[sudo] password for scott:                                                                                                                                             
Installing /usr/local/share/perl/5.10.0/AnyEvent.pm                                                                                                                    
Installing /usr/local/share/perl/5.10.0/Video/DVDRip.pm                                                                                                                
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/splash.en.png                                                                                                     
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/SrtxFile.pm                                                                                                       
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Subtitle.pm                                                                                                       
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/splash.da.png                                                                                                     
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/FilterList.pm                                                                                                     
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/icon.xpm                                                                                                          
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/splash.de.png                                                                                                     
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/splash.ca.png                                                                                                     
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/InfoFile.pm                                                                                                       
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/BitrateCalc.pm                                                                                                    
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/JobPlanner.pm                                                                                                     
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/splash.sr.png                                                                                                     
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Preset.pm                                                                                                         
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/TranscodeRC.pm                                                                                                    
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Convert.pm                                                                                                        
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Project.pm                                                                                                        
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Audio.pm                                                                                                          
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Title.pm                                                                                                          
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/splash.es.png                                                                                                     
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/translators.txt                                                                                                   
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/FilterSettings.pm                                                                                                 
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/splash.it.png                                                                                                     
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/PSU.pm                                                                                                            
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Depend.pm                                                                                                         
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/splash.sr@Latn.png                                                                                                
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Content.pm                                                                                                        
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Probe.pm                                                                                                          
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Logger.pm                                                                                                         
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Base.pm                                                                                                           
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/license.txt                                                                                                       
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Config.pm                                                                                                         
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Preview.pm                                                                                                    
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Pipe.pm                                                                                                       
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/ExecFlow.pm                                                                                                   
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/ZoomCalculator.pm                                                                                             
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/BitrateCalc.pm                                                                                                
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/MultiAudio.pm                                                                                                 
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Filters.pm                                                                                                    
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Context.pm                                                                                                    
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Rules.pm                                                                                                      
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Preferences.pm                                                                                                
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Depend.pm                                                                                                     
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Base.pm                                                                                                       
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Progress.pm                                                                                                   
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Main.pm                                                                                                       
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Project/Storage.pm                                                                                            
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Project/Subtitle.pm                                                                                           
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Project/ClipZoom.pm                                                                                           
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Project/Logging.pm                                                                                            
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Project/Transcode.pm                                                                                          
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Project/Title.pm                                                                                              
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/FormFactory/ClipImage.pm                                                                                      
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/FormFactory/SubtitlePreviews.pm                                                                               
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Cluster/Node.pm                                                                                               
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Cluster/Title.pm                                                                                              
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Cluster/Control.pm                                                                                            
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Icons/dvdrip-scan-volume.png                                                                                  
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Icons/dvdrip-audio-matrix.png                                                                                 
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Icons/dvdrip-play-movie.png                                                                                   
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Icons/dvdrip-clip-move.png                                                                                    
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Icons/dvdrip-calc-width.png                                                                                   
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/GUI/Icons/dvdrip-calc-height.png                                                                                  
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Term/ExitTask.pm                                                                                                  
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Term/Progress.pm                                                                                                  
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Term/Main.pm                                                                                                      
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Cluster/Webserver.pm                                                                                              
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Cluster/Master.pm                                                                                                 
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Cluster/Node.pm                                                                                                   
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Cluster/Pipe.pm                                                                                                   
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Cluster/ExecFlowFrontend.pm                                                                                       
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Cluster/JobPlanner.pm                                                                                             
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Cluster/Project.pm                                                                                                
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Cluster/Title.pm                                                                                                  
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Cluster/PSU.pm                                                                                                    
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/Cluster/Scheduler.pm                                                                                              
Installing /usr/local/share/perl/5.10.0/Video/DVDRip/CPAN/Scanf.pm                                                                                                     
Installing /usr/local/share/perl/5.10.0/Event/ExecFlow.pm                                                                                                              
Installing /usr/local/share/perl/5.10.0/Event/RPC.pm                                                                                                                   
Installing /usr/local/share/perl/5.10.0/Event/ExecFlow/Job.pm                                                                                                          
Installing /usr/local/share/perl/5.10.0/Event/ExecFlow/Frontend.pm                                                                                                     
Installing /usr/local/share/perl/5.10.0/Event/ExecFlow/Callbacks.pm                                                                                                    
Installing /usr/local/share/perl/5.10.0/Event/ExecFlow/Scheduler.pm                                                                                                    
Installing /usr/local/share/perl/5.10.0/Event/ExecFlow/Job/Group.pm                                                                                                    
Installing /usr/local/share/perl/5.10.0/Event/ExecFlow/Job/Code.pm                                                                                                     
Installing /usr/local/share/perl/5.10.0/Event/ExecFlow/Job/Command.pm                                                                                                  
Installing /usr/local/share/perl/5.10.0/Event/ExecFlow/Scheduler/SimpleMax.pm                                                                                          
Installing /usr/local/share/perl/5.10.0/Event/ExecFlow/Frontend/Term.pm                                                                                                
Installing /usr/local/share/perl/5.10.0/Event/RPC/Loop.pm                                                                                                              
Installing /usr/local/share/perl/5.10.0/Event/RPC/LogConnection.pm                                                                                                     
Installing /usr/local/share/perl/5.10.0/Event/RPC/Client.pm                                                                                                            
Installing /usr/local/share/perl/5.10.0/Event/RPC/Connection.pm                                                                                                        
Installing /usr/local/share/perl/5.10.0/Event/RPC/Message.pm                                                                                                           
Installing /usr/local/share/perl/5.10.0/Event/RPC/AuthPasswdHash.pm                                                                                                    
Installing /usr/local/share/perl/5.10.0/Event/RPC/Server.pm                                                                                                            
Installing /usr/local/share/perl/5.10.0/Event/RPC/Logger.pm                                                                                                            
Installing /usr/local/share/perl/5.10.0/Event/RPC/Loop/Event.pm                                                                                                        
Installing /usr/local/share/perl/5.10.0/Event/RPC/Loop/Glib.pm                                                                                                         
Installing /usr/local/share/perl/5.10.0/LocaleData/sr@Latn/LC_MESSAGES/video.dvdrip.mo                                                                                 
Installing /usr/local/share/perl/5.10.0/LocaleData/de/LC_MESSAGES/video.dvdrip.mo                                                                                      
Installing /usr/local/share/perl/5.10.0/LocaleData/sr/LC_MESSAGES/video.dvdrip.mo                                                                                      
Installing /usr/local/share/perl/5.10.0/LocaleData/es/LC_MESSAGES/video.dvdrip.mo                                                                                      
Installing /usr/local/share/perl/5.10.0/LocaleData/cs/LC_MESSAGES/video.dvdrip.mo                                                                                      
Installing /usr/local/share/perl/5.10.0/LocaleData/da/LC_MESSAGES/video.dvdrip.mo                                                                                      
Installing /usr/local/share/perl/5.10.0/LocaleData/it/LC_MESSAGES/video.dvdrip.mo                                                                                      
Installing /usr/local/share/perl/5.10.0/LocaleData/fr/LC_MESSAGES/video.dvdrip.mo                                                                                      
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory.pm                                                                                                         
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Popup.pm                                                                                                   
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Menu.pm                                                                                                    
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Button.pm                                                                                                  
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/YesNo.pm                                                                                                   
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/CheckButtonGroup.pm                                                                                        
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Loader.pm                                                                                                  
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/List.pm                                                                                                    
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Image.pm                                                                                                   
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/ExecFlow.pm                                                                                                
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Form.pm                                                                                                    
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/ProxyBuffered.pm                                                                                           
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/CheckButton.pm                                                                                             
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Expander.pm                                                                                                
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/DialogButtons.pm                                                                                           
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/VSeparator.pm                                                                                              
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/ProgressBar.pm                                                                                             
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/HBox.pm                                                                                                    
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/HSeparator.pm                                                                                              
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Widget.pm                                                                                                  
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/GtkWidget.pm                                                                                               
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/VPaned.pm                                                                                                  
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Combo.pm                                                                                                   
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/ToggleButton.pm                                                                                            
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Notebook.pm                                                                                                
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/RadioButton.pm                                                                                             
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Context.pm                                                                                                 
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Intro.pm                                                                                                   
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/TextView.pm                                                                                                
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Rules.pm                                                                                                   
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Layout.pm                                                                                                  
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Window.pm                                                                                                  
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Timestamp.pm                                                                                               
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Label.pm                                                                                                   
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/VBox.pm                                                                                                    
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Container.pm                                                                                               
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Table.pm                                                                                                   
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Entry.pm                                                                                                   
Installing /usr/local/share/perl/5.10.0/Gtk2/Ex/FormFactory/Proxy.pm                                                                                                   
Installing /usr/local/share/perl/5.10.0/AnyEvent/Impl/Event.pm                                                                                                         
Installing /usr/local/share/perl/5.10.0/AnyEvent/Impl/Glib.pm                                                                                                          
Installing /usr/local/share/perl/5.10.0/AnyEvent/Impl/Coro.pm                                                                                                          
Installing /usr/local/share/perl/5.10.0/AnyEvent/Impl/Tk.pm                                                                                                            
Installing /usr/local/man/man1/dvdrip-splitpipe.1p                                                                                                                     
Installing /usr/local/man/man1/dvdrip.1p                                                                                                                               
Installing /usr/local/man/man1/dvdrip-progress.1p                                                                                                                      
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Menu.3pm                                                                                                         
Installing /usr/local/man/man3/Event::ExecFlow::Job::Group.3pm                                                                                                         
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Rules.3pm                                                                                                        
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Window.3pm                                                                                                       
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::RadioButton.3pm                                                                                                  
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::HBox.3pm                                                                                                         
Installing /usr/local/man/man3/Event::RPC::Connection.3pm                                                                                                              
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Container.3pm                                                                                                    
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Widget.3pm                                                                                                       
Installing /usr/local/man/man3/Event::ExecFlow::Callbacks.3pm                                                                                                          
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Entry.3pm                                                                                                        
Installing /usr/local/man/man3/Event::RPC::Logger.3pm                                                                                                                  
Installing /usr/local/man/man3/Event::RPC::Server.3pm                                                                                                                  
Installing /usr/local/man/man3/Event::RPC::Loop::Event.3pm                                                                                                             
Installing /usr/local/man/man3/Event::RPC::LogConnection.3pm                                                                                                           
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::CheckButtonGroup.3pm                                                                                             
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Image.3pm                                                                                                        
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Context.3pm                                                                                                      
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::YesNo.3pm                                                                                                        
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Timestamp.3pm                                                                                                    
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::CheckButton.3pm                                                                                                  
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Layout.3pm                                                                                                       
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::ExecFlow.3pm                                                                                                     
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Notebook.3pm                                                                                                     
Installing /usr/local/man/man3/Event::RPC::Loop::Glib.3pm                                                                                                              
Installing /usr/local/man/man3/Event::ExecFlow::Job::Code.3pm                                                                                                          
Installing /usr/local/man/man3/Event::RPC::Message.3pm                                                                                                                 
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::DialogButtons.3pm                                                                                                
Installing /usr/local/man/man3/Event::ExecFlow::Frontend.3pm                                                                                                           
Installing /usr/local/man/man3/AnyEvent.3pm                                                                                                                            
Installing /usr/local/man/man3/Video::DVDRip.3pm                                                                                                                       
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::ProxyBuffered.3pm                                                                                                
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Form.3pm                                                                                                         
Installing /usr/local/man/man3/Event::ExecFlow.3pm                                                                                                                     
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::VBox.3pm                                                                                                         
Installing /usr/local/man/man3/Video::DVDRip::CPAN::Scanf.3pm                                                                                                          
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Loader.3pm                                                                                                       
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Button.3pm                                                                                                       
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Label.3pm                                                                                                        
Installing /usr/local/man/man3/Event::ExecFlow::Job.3pm                                                                                                                
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::List.3pm                                                                                                         
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Combo.3pm                                                                                                        
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory.3pm                                                                                                               
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::TextView.3pm                                                                                                     
Installing /usr/local/man/man3/Event::ExecFlow::Scheduler.3pm                                                                                                          
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Expander.3pm                                                                                                     
Installing /usr/local/man/man3/Event::ExecFlow::Job::Command.3pm                                                                                                       
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Popup.3pm                                                                                                        
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::GtkWidget.3pm                                                                                                    
Installing /usr/local/man/man3/Event::RPC::Loop.3pm                                                                                                                    
Installing /usr/local/man/man3/Event::RPC.3pm                                                                                                                          
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Table.3pm                                                                                                        
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::HSeparator.3pm                                                                                                   
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::VSeparator.3pm                                                                                                   
Installing /usr/local/man/man3/Event::ExecFlow::Scheduler::SimpleMax.3pm                                                                                               
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::ProgressBar.3pm                                                                                                  
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::ToggleButton.3pm                                                                                                 
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Intro.3pm                                                                                                        
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::VPaned.3pm                                                                                                       
Installing /usr/local/man/man3/Gtk2::Ex::FormFactory::Proxy.3pm                                                                                                        
Installing /usr/local/man/man3/Event::RPC::Client.3pm                                                                                                                  
Installing /usr/local/bin/dvdrip                                                                                                                                       
Installing /usr/local/bin/dvdrip-splitpipe                                                                                                                             
Installing /usr/local/bin/dvdrip-thumb                                                                                                                                 
Installing /usr/local/bin/dvdrip-master                                                                                                                                
Installing /usr/local/bin/dvdrip-exec                                                                                                                                  
Installing /usr/local/bin/dvdrip-splash                                                                                                                                
Installing /usr/local/bin/execflow                                                                                                                                     
Installing /usr/local/bin/dvdrip-replex
Installing /usr/local/bin/dvdrip-subpng
Installing /usr/local/bin/dvdrip-multitee
Installing /usr/local/bin/dvdrip-progress
Writing /usr/local/lib/perl/5.10.0/auto/Video/DVDRip/.packlist
Appending installation info to /usr/local/lib/perl/5.10.0/perllocal.pod
   
Any help would be appreciated

---

### Post by SuperSonic4 on 2010-01-29
So what is the actual error message? To me that looks like it installed as it should albeit to /usr/local which is common for compiled programs

What happens if you run ```
/usr/local/bin/dvdrip
```


edit: why not use k9copy if you're on kubuntu or handbrake if you want CLI/easy h264 encoding? Both are better than dvdrip IMO

---

### Post by SGC622 on 2010-01-29
This is what happens
>     
scott@Home:~$ /usr/local/bin/dvdrip
Can't locate Locale/TextDomain.pm in @INC (@INC contains: lib /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/local/bin/dvdrip line 36.
BEGIN failed--compilation aborted at /usr/local/bin/dvdrip line 36.
Can't locate Locale/TextDomain.pm in @INC (@INC contains: lib /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/local/bin/dvdrip-splash line 8.
BEGIN failed--compilation aborted at /usr/local/bin/dvdrip-splash line 8.


---

