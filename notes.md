# redhat_notes
self revised redhat rhcsa notes 
rhel vacation 124.txt
 
REDHAT ENTERPRISE LINUX CHAPTERS
LINUX
CLI
	ACCESSING CLI IN TEXT INTERFACE AND DESKTOP ENVIRONMENT 
		command LINE:Text based interface to run programs using commands
		shell:the program that makes cli possible takes commands run as input and interlink with kernel
		bash,zsh,
			#- Interactive Shells: Used directly by users for command execution (e.g., bash, zsh).
			#- Login Shells: Invoked at login, initialize environment variables.
			#- Non-Interactive Shells: Run scripts without user interaction.
			#- Restricted Shells: Limit user capabilities for security (e.g., rbash).
 
		terminal:text based interface to enter commands into and print output from computer system like putty session on which shell starts
		shell prompt ($ vs #)
		shell basics:comand-program to run; options preceded by - or --; arguements targets over which program has to run
	EXECUTING COMMANDS IN BASH SHELL
			shell basics:command-program to run; options preceded by - or --; arguements targets over which program has to run
			metacharacters in shell: bash : ; used for seperating commands
			useful tricks
			simple commands examples date; passwd ;file ;
			usage of tab;  backslash\ at end of line shell acknowledges continuation of coand by >
			history ;!command number
			upsrrow down arrow to run preivious commands
			alt+. last arguement of previously typed command
			
			ctrl+a ctrl+e  jump to beginning and end in command line
			ctrl+u ctrl+k  clear from cursor to beginning clear from cursor to end of command line
			ctrl+-> ctrl + <- move to end of next word and move to start of previous word
	
			
			
			
			
 
 
HELP-DOUCMENTATIONREDHAT SUPPORT
	man pages shipped with packages;located in /usr/share/man
		sections
		1.user commands
		2.system calls
		3.library functions
		
		4.special files
		5.file formats
		
		6.games screensavers
		
		7.convention standards and miscellaneou
		8.system administration and previliged commands
		
		9.linux kernel api
	for example
	passwd(1):passwd command 
	passwd(2):/etc/passwd user account file format
	
	man comand shows in alpha numeric order
	man section topic
 
	man page headings:
		NAME
		SYNOPSIS
		DESCRIPTION
		OPTIONS
		EXAMPLES
		FILES
		SEE ALSO
		BUGS
		AUTHOR
 
	USEFUL TRICKS in man page navigation
		UP-ARROW DOWN-ARROW one line at a time
		space bar one screen at a time
		/string n shift+n searching;next entry;previous entry respectively
		g and shift+g beginning and end respectively
	
	man -k topic :search for manpages with topic in their names and description
	man -K topic :search with manpages in whole not only in title not only in description
	
REDHAT SUPPORT
AI ASSISTNANCE
 
FILESYSTEM HIERARCHY
	Filesystem hierarchy
		inverted file-system hierarchy
		/ forward slash  is used for seperating the subdirectories
		/--> important sub directories of root folder for ease of detection and purpose
			/boot--> boot process files
			/etc--> persistent configuration files
			/dev-->files used for hardware 
			/root--> home dir of root user
			/home--> contains all home directories except root user
			/usr--> contains libraries system binaries and user installed binary
			/var--> used to store persistent data that  changes dynamically
			/run--> used to store non persistent data
			/tmp vs /var/tmp-->used to store temoprary files for 10 days and 30 days respectively
			
	filesystem navigation
	path naming files in linux -->absolute paths and relative paths
		absolute paths :unique file-system location--> start with /
		relative paths: : identifies a unique location, and specifies only the necessary path to reach the location from the working directory--> dont start with / if relative ;useful cmd for this pwd 
			use of quotes if filenames have spaces
			Users and processes change to other directories as needed
			ext4 and XFS, are case-sensitive--> my.txt is different from My.txt
			~ tilde represents present users home directory
			 
			ls -->list all files opions -l -a -r -t -data
			hidden files purpose :prevent one user's configuration from being accidentally copied to other directories or users
			
			cd . --> dot represents present working directory
			cd .. parent directory
			cd -		--> navigates to directory which we are using before immediately
			
			touch command creates file if not present and updates the time stamp of a file to the current date and time without otherwise modifying it
			
					
FILEMANAGEMENT
			creating files and directories
				mkdir
				mkdir -p --> mkdir parent directory i paent directory if not exists
				redirection from  cat and echo commands piping and teeing 
			removing files and directories
				rmdir removing empty directory
				rm -r used with recursive option before removing direcory interal directories are removed
				rm -f  forces the removal without prompting the user for confirmation
				rm command -i option to interactively prompt for confirmation before deleting.This option is essentially the opposite of using the rm command -f option, which forces the removal without prompting the user for confirmation
				A trash bin eature like  in windows is a component of a desktop environment such as GNOME, but is not used by commands that are run from a shell
			copying  files and directories
				copying files and sdirectory last argument mentioned taken as target location
				By default, the cp command does not copy directories
				cp -r  recurisive used to copy non emty directories
			moving and renaming files and directories
				moving files from one location to other
				moving file in same location only updates the file name
				
				
			links
				multiple filenames pointing same filenames
				A hard link points a name to data on a storage device.
				A symbolic link points a name to another name, which points to data on a storage device.
				hardlinks
					multiple filenames pointing same data,if we edit one hardlink other changes reflected in other ;same inode number  --> 
					ls -l output second column gives  link count
					Hard links that reference the same file share the inode structure with the link count, access permissions, user and group ownership, time stamps, and file content.When that information is changed for one hard link, the other hard links for the same file also show the new information
					Data is deleted from storage only when the last hard link is deleted
					can be used only with regular file snot with special files(files pointing to devices inerfaces and other files not containing regular data) and directories  and can be created only same filesystem
						ln  filename hardlink name
				softlinks
					ln -s filename softlinknam
					ls -l output first column first dash turns to l symbolising soft link or symbolic link
					if original file is lost data is lost but symbolic link present dangling with no actual data
					One side effect of the dangling symbolic link in the preceding example is that if you create a file with the same name as the deleted file (/home/user/newfile-link2.txt), then the symbolic link  is no longer "dangling" and points to the new file. 
					update the current working directory by using the name of the actual directory instead of linkname, then you can use the -P option.
					
					
			Matching File Names with Shell Expansions
					Pathname expansion, which helps to select one or more files by pattern matching.globbing/.wild card charcters.If the pattern does not match anything, then the shell tries to use the pattern as a literal argument for the command that it runs.
						Pattern	Matches
							*	Any string of zero or more characters
							?	Any single character
							[abc…​]	Any one character in the enclosed class (between the square brackets)
							[!abc…​]	Any one character not in the enclosed class
							[^abc…​]	Any one character not in the enclosed class
							[[:alpha:]]	Any alphabetic character
							[[:lower:]]	Any lowercase character
							[[:upper:]]	Any uppercase character
							[[:alnum:]]	Any alphabetic character or digit
							[[:punct:]]	Any printable character that is not a space or alphanumeric
							[[:digit:]]	Any single digit from 0 to 9
							[[:space:]]	Any single white space character, which might include tabs, newlines, carriage returns, form feeds, or spaces
							Use [^...] for regex.
							Use [!... ] for filename patterns in shells (like bash).
					Brace expansion, which can generate multiple strings of characters.
						Brace expansion generates discretionary strings of characters. Braces contain a comma-separated list of strings, or a sequence of expression. The result includes the text that precedes or follows the brace definition. Brace expansions might be nested, one inside another. You can also use double-dot syntax (..), which expands to a sequence.
						{m..p} double-dot syntax inside braces expands to m n o p.
					Tilde expansion, which expand to a path to a user home directory.
						The Bash shell executes the home directory substitution based on a few factors. If the tilde is followed by a string of characters other than a forward slash (/), then the shell interprets the string up to that slash as a username. If the substring matches an actual username, then the shell replaces the string with the absolute path to that user's home directory. If the substring does not match a username, then the shell uses an actual tilde followed by the string of characters.
					Variable expansion, which replaces text with the value that is stored in a shell variable.
					Command substitution, which replaces text with the output of a 
						enables the output of a command to replace the command itself on the command line. Command substitution occurs when you enclose a command in parentheses and precede it by a dollar sign ($). 
						earlier form of command substitution uses backticks: `command`. Although the Bash shell still accepts this format
						
					prevent shell expansions on parts of your command line, you can quote and escape characters and strings.
					The backslash (\) is an escape character in the Bash shel
					Single quotation marks stop all shell expansion. Double quotation marks stop most shell expansion.
					Double quotation marks suppress special characters other than the dollar sign ($), backslash (\), backtick (`), and exclamation point (!) from operating inside the quoted text. Double quotation marks block pathname expansion, but still allow command substitution and variable expansion to occur.


	
			
			
			

 
TEXT FILESYSTEM
vim editor offers various modes of operation such as command mode, extended command mode, edit mode, and visual mode. As a Vim user, always verify the current mode, because the effect of keystrokes varies between modes.
mode of operaion:		insert|command								   |extended command mode|visual mode
keystrokes of operation:i	  |	 default mode-esc if youre in any mode |:					 |ctrl-v V shift+v
REDIRECTING
			A process uses numbered channels named file descriptors to get input and to send output. All processes start with at least three file descriptors.
			Standard input (channel 0) reads input from the keyboard.
			Standard output (channel 1) sends regular system output to the terminal.
			Standard error (channel 2) sends error messages to the terminal.
			If a program opens separate connections to other files, then it might use file descriptors with higher numbers.
			>
			>>
			2>/dev/null
			>>file1 2>&1
			2>/dev/null
			
			pipeline
			| redirects output of one command to input of other command
			
			tee command used to redirect and copies output to terminal
			
			
USERS GROUPS
for security boundaries and maintaining lowest previliged access required to work
human userssystem users -uids
super user uid=0 root account has all access ;system user used by sytem processes and daemons; regular user

file ownership;processes running as which determines files accessible to that process'

mapping of uids to uses internal user dattabases--> .etc.passwd local use information
	passwd file entry-->username:x{placeholder for password}:usenameshortinfo:uid:gid:homedir:default shell 
	/sbin/nologin shell to disallow interactive logins with that account
	
	
Group collection of users those shae system resources and file permissions
	gids
	group info in identity management databases/local group info stored in /etc/group
		groupname:x:gid:memberusers
	primary group:group ceated when user created in which only use is parts
	supplementary group of which user is member other than primary
	id command gives infoand group file also have info on membership groups which user is member of
	
	

switching user acount
usage of su :usage of su with user account and without user account
			 usage of su with hyphen (login shell) without hyphen(non login shell)

sudo:run as  user:provide users password who is running not root password if running as root:
	 sudo is to log by default all the executed commands to /var/log/secure
	sudo -u username command

Red Hat Enterprise Linux 7 and later versions, all members of the wheel group can use sudo to
run commands as any user, including root, by using their own password
	Historically, UNIX systems use membership of the wheel group to grant or control
superuser access. RHEL 6 and earlier versions do not grant the wheel group any
special privileges by default. System administrators who previously used this group
for a non-standard purpose must update a previous configuration, to prevent
unexpected and unauthorized users from obtaining administrative access on
RHEL 7 and later systems
	We “need” sudo -i and sudo -s because they combine the behavior of su/su - with the security model of sudo. That way, administrators don’t have to share the root password, 

	
	/etc/sudoers file
		use visudo to edit
		/etc/sudoers file also includes the contents of any files in the /etc/
		sudoers.d directory as part of the configuration file. With this hierarchy, you can add sudo access for a user by putting an appropriate file in that directory.
		#includedir /etc/sudoers.d
		- That line tells sudo to read in all files inside /etc/sudoers.d as if their contents were part of /etc/sudoers.



		entry formats in sudoers file
		%WHEEL ALL=(ALL:ALL) ALL
		USER ALL=(ALL) ALL
		- Here, the first ALL means “on all hosts.” Since you’re only on one host, it effectively means “on this machine.”
		- In larger environments (like with NIS/LDAP or centrally managed sudoers), you can specify hostnames:
		alice myserver=(ALL) ALL
		bob workstation1,workstation2=(ALL) /usr/bin/systemctl restart apache2
		The ALL=(ALL:ALL) command specifies that on any host with this file (the first ALL), users in
		the wheel group can run commands as any other user (the second ALL) and as any other group
		(the third ALL) on the system.
		The final ALL command specifies that users in the wheel group can run any command		
	
		set up sudo to allow a user to run commands as another user without entering their
password, by using the NOPASSWD: ALL command:
ansible        ALL=(ALL)       
NOPASSWD: ALL
	
	
	
usermanagement
	useradd user creation we can specify options to override default user properties like uid homedirectory primary gid
	usermod modify created  user chars
	Option | Long Form 		   | Purpose 													| Example
	-------|-------------------|------------------------------------------------------------|-------------------------------------------------------
	-a     | --append  		   | Append supplementary groups (must be used with -G) 		| usermod -a -G wheel alice
	-c     | --comment COMMENT | Set/change the comment field (often full name/description) | usermod -c "Alice Johnson, Developer" alice
	-d     | --home HOME_DIR   | Change the user’s home directory 							| usermod -d /srv/alice_home alice
	-g     | --gid GROUP       | Set the primary group for the user 						| usermod -g developers alice
	-G     | --groups GROUPS   | Set supplementary groups (comma-separated list) 			| usermod -G wheel,developers alice
	-L     | --lock            | Lock the account (disables login) 							| usermod -L alice
	-m     | --move-home       | Move home directory to new location (use with -d) 			| usermod -d /srv/alice_home -m alice
	-s     | --shell SHELL     | Change login shell 										| usermod -s /bin/zsh alice
	-U     | --unlock          | Unlock a previously locked account 						| usermod -U alice
	/etc/login.defs managing possible default characteristics of new users about tobe created range of uids and paswod aging specs etc.,
	
	userdel:deleted use account without removing home directory
	userdel -r removes user directoy along with home directory
	
	passwd username:changes user password
	
	
group management
	group add creates group with group id which is one higher than max available gid from range gid_max and gid_min defined in login.defs
	groupadd -r which is used to create groups with system groups
	groupmod -n used to change groupname
	groupmod -G used to change used to change gid
	group del used to deleted group:we cant delete group if its primary group of one user
ACCESS

chmod 
 
SOFTWARE PACKAGES
FLATPAK?
 
REMOVABLE MEDIA
 
 
PROCESSES
SERVICES AND DAEMONS
 
CONFIGURING AND SECURING SSH
 
