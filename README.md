# Restaurante Fahiteiro — site oficial

Site responsivo para o Restaurante Fahiteiro, Huambo, com página pública e painel de administração ligado ao Supabase.

## Ficheiros
- `index.html`: página pública.
- `admin.html`: painel para editar textos, imagens, logótipo e pratos.
- `config.js`: configuração do Supabase (não contém segredos).
- `supabase/schema.sql`: tabelas, políticas de acesso e armazenamento de imagens.

## Configuração necessária para activar o painel privado
1. Cria um projecto em https://supabase.com/ e abre o **SQL Editor**.
2. Copia e executa todo o conteúdo de `supabase/schema.sql`.
3. Em **Project Settings → API** (ou Connect), copia a Project URL e a chave publicável/anon.
4. Edita `config.js` e coloca esses dois valores em `FAHITEIRO_SUPABASE_URL` e `FAHITEIRO_SUPABASE_ANON_KEY`. Nunca coloques a chave `service_role` no frontend.
5. Em **Authentication → Users**, cria o utilizador que será o administrador. Desactiva o registo público de utilizadores nas definições de Authentication.
6. Copia o UUID desse utilizador e executa no SQL Editor, substituindo o exemplo:
   `insert into public.profiles (id, role) values ('UUID-DO-UTILIZADOR', 'admin');`
7. Publica os ficheiros num alojamento estático HTTPS (por exemplo, GitHub Pages). O GitHub guarda o código; o Supabase trata da autenticação, base de dados e imagens.

## Importante
- O painel não aceita acesso sem autenticação Supabase e verifica o papel `admin`.
- O menu começa sem pratos reais; adiciona nomes e preços confirmados pelo restaurante no painel.
- O contacto telefónico e horário não foram incluídos porque ainda não foram confirmados.
- A página pública mostra texto e imagens iniciais até o Supabase ser configurado.
