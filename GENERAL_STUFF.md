# for windows:
everything search: https://www.voidtools.com/
filepilot: https://filepilot.tech/
dowload youtube videos (måste ha ffmpeg i pathen): https://github.com/yt-dlp/yt-dlp  https://ffmpeg.org/
autohotkey: https://www.autohotkey.com/
raddbg: https://github.com/EpicGamesExt/raddebugger

# setup c programming (det här är det värsta jag någonsin gjort)
för att kunna köra cl behöver visual studio och allt vara i pathen. För det måste man öppna vscode i developer terminal. Men man kan även lägga in det i vscode tasken. Detta är ett exempel på hur jag bygger c projektet: 
	"tasks": {
		"version": "1.0.0",
		"windows": {
			"options": {
				"shell": {
					"executable": "cmd.exe",
					"args": [
						"/C",
						// The path to VsDevCmd.bat depends on the version of Visual Studio you have installed.
						"\"C:/Program Files/Microsoft Visual Studio/2022/Community/Common7/Tools/VsDevCmd.bat\"",
          				"-arch=x64",
						"&&"
					]
				}
			}
		},
		"tasks": [
			{
				"label": "Build C/C++ Project (Debug)",
				"type": "shell",
				//"command": "where cl",
				"command": "cl /Zi /EHsc /Fe:bin\\${fileBasenameNoExtension}_debug.exe /Fo:bin\\ /Fd:bin\\ ${file}",
				"group": {
					"kind": "build",
					"isDefault": true
				},
				"problemMatcher": [
					"$msCompile"
				],
				"presentation": {
					"reveal": "always"
				},
				"detail": "Build with MSVC cl compiler in debug mode (/Zi)"
			},
		]
	},



# useful commands: 
(använd url till playlist för att ladda ned playlist) om det har special karaktärer som "&" i urlen måste man använda quotes runt urlen
yt-dlp https://www.youtube.com/watch?v=DYWTw19_8r4
eller för flera videos
yt-dlp -P 2 https://www.youtube.com/watch?v=DYWTw19_8r4 https://www.youtube.com/watch?v=DYWTw19_8r4
för hel spellista:


Hämtar alla hemsidor från en url. Väldigt bra om man vill kunna se blogar och liknande själv senare när man inte har internet. Måste ha windows versionen av wget https://eternallybored.org/misc/wget/

wget --mirror --convert-links --adjust-extension --page-requisites --no-parent https://benhoyt.com/writings/


create symlinks (måste köras i command prompt). detta är de jag använder för den här konfigurationen:
mklink C:\Users\vsslow\AppData\Roaming\Code\User\settings.json C:\programming\configuration\vscode_conf\settings.json
mklink C:\Users\vsslow\AppData\Roaming\Code\User\keybindings.json C:\programming\configuration\vscode_conf\keybindings.json


# felsökning
## om terminalen inte uppdateras när du ändrar enviroment variables. OBS! vet inte om detta faktiskt göra någonting. verkade fuucka upp allt
Kör detta i terminalen: [Environment]::SetEnvironmentVariable("Path", $env:Path + ";C:\Users\vsslow\Downloads\ffmpeg-7.1.1-essentials_build\ffmpeg-7.1.1-essentials_build\bin\", "User")


# TODO att fixa:
code action
make jk useable on long wrapped lines
gl to select multiple of same word (smart rename) fun
gör så att ctrl-shift hjkl går till olika paneler. Nu kan jag typ inte gå till terminalen
