# Detalhes Artesanais — app do ateliê (PWA)

## Publicar no GitHub Pages
1. Crie um repositório novo (ex.: `atelie`) no GitHub.
2. Envie TODOS os arquivos desta pasta (index.html, manifest.json, sw.js, firebase-config.js e a pasta icons).
3. Settings > Pages > Branch `main` / pasta `/ (root)` > Save.
4. Abra `https://SEU-USUARIO.github.io/atelie/` no celular e escolha "Adicionar à tela inicial".

## Sincronizar entre aparelhos (opcional, Firebase gratuito)
1. No Firebase (pode ser o mesmo projeto do app de finanças), em Configurações do projeto > Seus apps,
   copie o objeto `firebaseConfig` e cole em `firebase-config.js` no lugar de `null`.
2. Authentication > Método de login: Google ativado. Em "Domínios autorizados", confira se `SEU-USUARIO.github.io` está lá.
3. Firestore > Regras: ACRESCENTE este bloco dentro de `match /databases/{database}/documents { ... }`
   (sem apagar as regras que já existem):

       match /usuarios/{uid}/{doc=**} {
         allow read, write: if request.auth != null && request.auth.uid == uid;
       }

4. No app, vá em Mais > Configurações > Entrar com Google.
   Na primeira entrada, os dados que já estão no aparelho sobem para a nuvem.

## Backup
Mais > Configurações > Baixar backup (arquivo .json). Para restaurar, use "Restaurar backup".
